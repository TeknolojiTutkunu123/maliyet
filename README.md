<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8"> 
<title>Gram Paket Kahve Maliyet Hesaplama</title>
<style>
    body {
        font-family: Arial;
        background:#f4f4f4;
        padding:40px;
    }
    .container {
        background:white;
        padding:30px;
        max-width:600px;
        margin:auto;
        border-radius:10px;
        box-shadow:0 0 10px rgba(0,0,0,0.1);
    }
    input {
        width:100%;
        padding:8px;
        margin:5px 0 15px 0;
    }
    button {
        padding:10px;
        width:100%;
        background:#d32f2f;
        color:white;
        border:none;
        cursor:pointer;
    }
    .result {
        margin-top:20px;
        background:#f1f1f1;
        padding:15px;
    }
</style>
</head>
<body>

<div class="container">
    <h2>Gram Paket Kahve Maliyet Hesaplama</h2>

    <label>Kahve Maliyeti (TL)</label>
    <input type="number" id="kahve">

    <label>Jelatin Ambalaj (TL)</label>
    <input type="number" id="jelatin">

    <label>Diş Kutu Payi (TL)</label>
    <input type="number" id="kutu">

    <label>İşçilik + Fire (%)</label>
    <input type="number" id="iscilik">

    <label>Kira + Gider (%)</label>
    <input type="number" id="gider">

    <label>KDV (%)</label>
    <input type="number" id="kdv">

    <button onclick="hesapla()">HESAPLA</button>

    <div class="result" id="sonuc"></div>
</div>

<script>
function hesapla(){
    let kahve = parseFloat(document.getElementById("kahve").value) || 0;
    let jelatin = parseFloat(document.getElementById("jelatin").value) || 0;
    let kutu = parseFloat(document.getElementById("kutu").value) || 0;
    let iscilik = parseFloat(document.getElementById("iscilik").value) || 0;
    let gider = parseFloat(document.getElementById("gider").value) || 0;
    let kdv = parseFloat(document.getElementById("kdv").value) || 0;

    let temelMaliyet = kahve + jelatin + kutu;

    let iscilikTutar = temelMaliyet * (iscilik/100);
    let giderTutar = temelMaliyet * (gider/100);

    let hamMaliyet = temelMaliyet + iscilikTutar + giderTutar;
    let kdvDahil = hamMaliyet * (1 + kdv/100);

    let kar10 = kdvDahil * 1.10;
    let kar20 = kdvDahil * 1.20;
    let kar30 = kdvDahil * 1.30;

    let koli10 = kar10 * 20;
    let koli20 = kar20 * 20;
    let koli30 = kar30 * 20;

    document.getElementById("sonuc").innerHTML = `
        <b>Ham Maliyet:</b> ${hamMaliyet.toFixed(2)} TL<br>
        <b>KDV Dahil Maliyet:</b> ${kdvDahil.toFixed(2)} TL<br><br>

        <b>%10 Kar:</b> ${kar10.toFixed(2)} TL (1 Koli: ${koli10.toFixed(2)} TL)<br>
        <b>%20 Kar:</b> ${kar20.toFixed(2)} TL (1 Koli: ${koli20.toFixed(2)} TL)<br>
        <b>%30 Kar:</b> ${kar30.toFixed(2)} TL (1 Koli: ${koli30.toFixed(2)} TL)
    `;
}
</script>

</body>
</html># maliyet
Web project
