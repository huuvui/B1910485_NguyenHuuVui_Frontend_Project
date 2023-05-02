<template>
    <header class="header">
        <h1>NOTES

            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <meta http-equiv="X-UA-Compatible" content="ie=edge">
            <link href="https://fonts.googleapis.com/css?family=Open+Sans&display=swap" rel="stylesheet">
            <link rel="stylesheet" href="style.css">
            <div id="container">
                <div id="dong_ho">
                    <div id="thoi_gian">
                        <div>
                            <span id="gio">00</span><span>Giờ</span>
                        </div>
                        <div>
                            <span id="phut">00</span><span>Phút</span>
                        </div>
                        <div>
                            <span id="giay">00</span><span>Giây</span>
                        </div>

                    </div>
                </div>
                <div class="lich">
                    <div id="days"></div>
                    <div id="dates"></div>
                </div>

            </div>
        </h1>
        
    </header>

    <body>

    </body>
</template>

<script>
export default {
    name: "Header",
};

function Dong_ho() {
    var gio = document.getElementById("gio");
    var phut = document.getElementById("phut");
    var giay = document.getElementById("giay");
    var Gio_hien_tai = new Date().getHours();
    var Phut_hien_tai = new Date().getMinutes();
    var Giay_hien_tai = new Date().getSeconds();
    gio.innerHTML = Gio_hien_tai;
    phut.innerHTML = Phut_hien_tai;
    giay.innerHTML = Giay_hien_tai;
}
var Dem_gio = setInterval(Dong_ho, 1000);

window.onload = setInterval(clock, 1000);
function clock() {
    var d = new Date();
    var date = d.getDate();
    var month = d.getMonth();
    var montharr = ["Tháng 1", "Tháng 2", "tháng 3", "Tháng 4", "Tháng 5", "Tháng 6", "Tháng 7", "Tháng 8", "Tháng 9", "Tháng 10", "tháng 11", "Tháng 12"];
    month = montharr[month];
    var year = d.getFullYear();
    var day = d.getDay();
    var dayarr = ["Chủ Nhật", "Thứ 2", "Thứ 3", "Thứ 4", "Thứ 5", "Thứ 6", "Thứ 7"];
    day = dayarr[day];
    document.getElementById("days").innerHTML = day;
    document.getElementById("dates").innerHTML = "Ngày" + " " + date + " " + month + " " + year;
}
</script>

<style scoped>
.header {
    background-image: url(https://mega.com.vn/media/news/2037_hinh_nen_thien_nhien_4k__28_.jpg);
    color: #fff;
    text-align: center;
    padding: 10px;
}

.lich {
    color: #f9f4f4;
    font-size: 20px;
    text-align: left;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Open Sans', sans-serif;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: #FFA17F;
    background: -webkit-linear-gradient(to right, #00223E, #FFA17F);
    background: linear-gradient(to right, #00223E, #FFA17F);
}

#dong_ho h2 {
    position: relative;
    display: block;
    color: #fff;
    text-align: center;
    margin: 10px 0;
    font-weight: 200;
    text-transform: uppercase;
    letter-spacing: 0.4em;
}

#dong_ho #thoi_gian div {
    position: relative;
    margin: 0 5px;
}

#dong_ho #thoi_gian {
    display: flex;
}

#dong_ho #thoi_gian div {
    position: relative;
    margin: 0 5px;
}

#dong_ho #thoi_gian div span {
    position: relative;
    display: block;
    width: 80px;
    height: 60px;
    background: #2196f3;
    color: #fff;
    font-weight: 120;
    display: center;
    justify-content: center;
    align-items: center;
    font-size: 3rem;
    z-index: 3;
    box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.2);
}

#dong_ho #thoi_gian span:nth-child(2) {
    height: 45px;
    font-size: 1rem;
    letter-spacing: 0.3rem;
    z-index: 2;
    box-shadow: none;
    background: #127fd6;
    text-transform: uppercase;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>

