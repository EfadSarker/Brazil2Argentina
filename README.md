```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Brazil to Argentina Registration Form</title>

<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, sans-serif;
}

body{
    background:#78a7dc;
    padding:30px;
    display:flex;
    flex-direction:column;
    align-items:center;
}

.form-container{
    width:900px;
    background:white;
    border:4px solid #5f95d4;
    border-radius:25px;
    padding:35px;
}

.header{
    display:flex;
    justify-content:space-between;
    align-items:flex-start;
}

.flag{
    width:140px;
}

.center-title{
    text-align:center;
    flex:1;
}

.center-title h1{
    color:#08286e;
    font-size:52px;
    font-weight:900;
}

.switch-text{
    margin-top:15px;
    font-size:34px;
    font-weight:900;
    line-height:1.3;
}

.brazil{
    color:#169541;
}

.argentina{
    color:#7fa9db;
}

.arrow{
    font-size:70px;
    color:#7fa9db;
}

.description{
    text-align:center;
    font-size:22px;
    margin:25px 0 35px;
}

.form-row{
    display:flex;
    align-items:center;
    margin-bottom:15px;
}

.form-row label{
    width:240px;
    font-size:20px;
    font-weight:800;
    color:#0d1d4f;
}

.form-row input,
.form-row textarea{
    flex:1;
    border:2px solid #d7d7d7;
    border-radius:8px;
    padding:12px;
    font-size:18px;
}

textarea{
    height:120px;
    resize:none;
}

.note{
    margin-left:240px;
    color:#777;
    font-size:14px;
}

.confirm{
    margin-top:20px;
    margin-left:240px;
    display:flex;
    align-items:center;
    gap:10px;
}

.confirm input{
    width:24px;
    height:24px;
}

.signature-section{
    display:flex;
    justify-content:space-between;
    margin-top:60px;
}

.sign-box{
    width:40%;
    text-align:center;
}

.line{
    border-top:2px solid #000;
    margin-bottom:10px;
}

.signature-font{
    font-family:'Great Vibes', cursive;
    font-size:42px;
    min-height:50px;
}

.date-display{
    font-size:20px;
    min-height:50px;
    padding-top:12px;
}

.footer{
    margin-top:40px;
    background:#eef5ff;
    padding:15px;
    text-align:center;
    border-radius:12px;
    font-weight:800;
    color:#0d1d4f;
}

.download-btn{
    margin-top:20px;
    padding:15px 35px;
    border:none;
    border-radius:8px;
    background:#0d4bb3;
    color:white;
    font-size:18px;
    cursor:pointer;
}

.download-btn:hover{
    opacity:.9;
}
</style>
</head>
<body>

<div id="formArea" class="form-container">

    <div class="header">

        <img class="flag"
        src="https://flagcdn.com/w320/br.png">

        <div class="center-title">

            <h1>REGISTRATION FORM</h1>

            <div class="switch-text">
                I'M SWITCHING<br>
                <span class="brazil">BRAZIL FAN</span>
                TO
                <span class="argentina">ARGENTINA FAN</span>
            </div>

            <div class="arrow">➜</div>

        </div>

        <img class="flag"
        src="https://flagcdn.com/w320/ar.png">

    </div>

    <div class="description">
        I, the undersigned, hereby declare my official decision
        to switch my allegiance from Brazil to Argentina.
    </div>

    <div class="form-row">
        <label>FULL NAME:</label>
        <input type="text" id="fullName">
    </div>

    <div class="form-row">
        <label>DATE OF BIRTH:</label>
        <input type="date">
    </div>

    <div class="form-row">
        <label>PREVIOUS ALLEGIANCE:</label>
        <input type="text" value="🇧🇷 BRAZIL">
    </div>

    <div class="form-row">
        <label>NEW ALLEGIANCE:</label>
        <input type="text" value="🇦🇷 ARGENTINA">
    </div>

    <div class="form-row">
        <label>DATE OF SWITCH:</label>
        <input type="date" id="switchDate">
    </div>

    <div class="form-row">
        <label>REASON FOR SWITCH:</label>
        <textarea></textarea>
    </div>

    <div class="note">
        (e.g. Messi effect, better football, passion, trophies, etc.)
    </div>

    <div class="confirm">
        <input type="checkbox">
        <span>I confirm that this decision is final and voluntary.</span>
    </div>

    <div class="signature-section">

        <div class="sign-box">
            <div class="line"></div>
            <div id="signatureText" class="signature-font"></div>
            <strong>SIGNATURE</strong>
        </div>

        <div class="sign-box">
            <div class="line"></div>
            <div id="switchDateText" class="date-display"></div>
            <strong>DATE</strong>
        </div>

    </div>

    <div class="footer">
        🏆 ONCE AN ARGENTINA FAN, ALWAYS AN ARGENTINA FAN.<br>
        VAMOS ARGENTINA! 🇦🇷
    </div>

</div>

<button class="download-btn" onclick="downloadForm()">
    Download Form
</button>

<script>

const fullNameInput = document.getElementById('fullName');
const switchDateInput = document.getElementById('switchDate');

fullNameInput.addEventListener('input', () => {
    document.getElementById('signatureText').innerText =
    fullNameInput.value;
});

switchDateInput.addEventListener('change', () => {

    if(!switchDateInput.value) return;

    const date = new Date(switchDateInput.value);

    const formatted =
        String(date.getDate()).padStart(2,'0') + '/' +
        String(date.getMonth()+1).padStart(2,'0') + '/' +
        date.getFullYear();

    document.getElementById('switchDateText').innerText =
    formatted;

});

function downloadForm(){

    html2canvas(document.getElementById('formArea'),{
        scale:2,
        useCORS:true
    }).then(canvas=>{

        const link = document.createElement('a');

        link.download =
        'Argentina-Fan-Registration-Form.png';

        link.href =
        canvas.toDataURL('image/png');

        link.click();

    });

}
</script>

</body>
</html>
```
