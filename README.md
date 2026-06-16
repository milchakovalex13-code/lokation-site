<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Определение местоположения</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

body{
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    background:linear-gradient(135deg,#667eea,#764ba2);
}

.card{
    width:400px;
    max-width:90%;
    background:white;
    border-radius:20px;
    padding:30px;
    text-align:center;
    box-shadow:0 15px 35px rgba(0,0,0,.2);
}

h1{
    color:#333;
    margin-bottom:15px;
}

p{
    color:#666;
    margin-bottom:20px;
}

button{
    background:#667eea;
    color:white;
    border:none;
    padding:15px 30px;
    border-radius:12px;
    cursor:pointer;
    font-size:16px;
    transition:.3s;
}

button:hover{
    transform:translateY(-2px);
}

.result{
    margin-top:20px;
    color:#333;
    line-height:1.8;
}
</style>
</head>
<body>

<div class="card">
    <h1>📍 Определение местоположения</h1>
    <p>Нажмите кнопку ниже, чтобы поделиться своей геолокацией.</p>

    <button onclick="getLocation()">
        Поделиться местоположением
    </button>

    <div id="result" class="result"></div>
</div>

<script>
function getLocation(){
    const result = document.getElementById("result");

    if(!navigator.geolocation){
        result.innerHTML = "Геолокация не поддерживается.";
        return;
    }

    result.innerHTML = "Получение данных...";

    navigator.geolocation.getCurrentPosition(
        (position)=>{
            result.innerHTML =
                `<b>Широта:</b> ${position.coords.latitude}<br>
                 <b>Долгота:</b> ${position.coords.longitude}<br><br>
                 <a href="https://maps.google.com/?q=${position.coords.latitude},${position.coords.longitude}" target="_blank">
                 Открыть на карте
                 </a>`;
        },
        ()=>{
            result.innerHTML = "Доступ к геолокации не предоставлен.";
        }
    );
}
</script>

</body>
</html>
