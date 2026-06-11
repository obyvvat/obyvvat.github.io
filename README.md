# obyvvat.github.io


<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Prototyp UX – Badanie</title>

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #0f172a;
    color: white;
}

.container {
    max-width: 420px;
    margin: auto;
    padding: 20px;
}

.card {
    background: #1e293b;
    padding: 16px;
    border-radius: 16px;
    margin-bottom: 12px;
}

h1 {
    font-size: 20px;
}

input {
    width: 100%;
    padding: 10px;
    margin: 6px 0;
    border-radius: 10px;
    border: none;
}

button {
    width: 100%;
    padding: 12px;
    margin-top: 10px;
    border-radius: 12px;
    border: none;
    background: #38bdf8;
    color: black;
    font-weight: bold;
    cursor: pointer;
}

button:hover {
    opacity: 0.9;
}

.profile-img {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    object-fit: cover;
    margin-bottom: 10px;
    border: 2px solid #38bdf8;
}

.hidden {
    display: none;
}

.tag {
    display: inline-block;
    background: #334155;
    padding: 6px 10px;
    border-radius: 10px;
    margin-top: 6px;
    font-size: 12px;
}
</style>
</head>

<body>

<div class="container">

<!-- FORM -->
<div id="formView">
    <div class="card">
        <h1>Prototyp badawczy UX</h1>
        <p class="tag">wyłącznie do celów naukowych</p>

        <input type="text" id="name" placeholder="Imię">
        <input type="text" id="surname" placeholder="Nazwisko">
        <input type="number" id="year" placeholder="Rok urodzenia">
        <input type="text" id="city" placeholder="Miasto">
        <input type="file" id="photo" accept="image/*">

        <button onclick="createProfile()">Zapisz i przejdź dalej</button>
    </div>
</div>

<!-- PROFILE -->
<div id="profileView" class="hidden">

    <div class="card" style="text-align:center;">
        <img id="outPhoto" class="profile-img">
        <h2 id="outName"></h2>
        <p id="outYear"></p>
        <p id="outCity"></p>
    </div>

    <div class="card">
        <h3>Panel użytkownika</h3>
        <p class="tag">Dane profilu</p>
        <p class="tag">Aktywność</p>
        <p class="tag">Ustawienia</p>
        <p class="tag">Preferencje</p>
    </div>

    <button onclick="reset()">Wróć</button>
</div>

</div>

<script>
function createProfile() {
    const name = document.getElementById("name").value;
    const surname = document.getElementById("surname").value;
    const year = document.getElementById("year").value;
    const city = document.getElementById("city").value;
    const file = document.getElementById("photo").files[0];

    document.getElementById("outName").innerText = name + " " + surname;
    document.getElementById("outYear").innerText = "Rok urodzenia: " + year;
    document.getElementById("outCity").innerText = "Miasto: " + city;

    if (file) {
        const reader = new FileReader();
        reader.onload = e => {
            document.getElementById("outPhoto").src = e.target.result;
        };
        reader.readAsDataURL(file);
    }

    document.getElementById("formView").classList.add("hidden");
    document.getElementById("profileView").classList.remove("hidden");
}

function reset() {
    document.getElementById("formView").classList.remove("hidden");
    document.getElementById("profileView").classList.add("hidden");
}
</script>

</body>
</html>
