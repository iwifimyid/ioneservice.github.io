## iPrint Tutorial Installasi

Aplikasi ini dibuat khusus untuk cetak voucher dari smartphone ke printer thermal bluetooth yang digenerate menggunakan userman mikrotik.

### Download [iPrint Free](https://play.google.com/store/apps/details?id=id.ioneservice.iprint.free)

Sebelum mencetak anda harus buat template voucher baru di user manager mikrotik. Proses pembuatan template voucher hanya sekali saja. Buat template dengan nama bebas atau misal iPrint App dan copy paste kode berikut:

### Pada kolom Header isikan kode atau script berikut:

```markdown
<!DOCTYPE html>
<html>
<head>
<title>iPrint App </title>
</head>
<body>
<script> 
function copyer(containerid) {
    var elt = document.getElementById(containerid);
    if (document.selection) { // IE
        if(elt.nodeName.toLowerCase() === "input"){
            document.getElementById(containerid).select();
            document.execCommand("copy");
        }else{
            var range = document.body.createTextRange();
            range.moveToElementText(document.getElementById(containerid));
            range.select();
            document.execCommand("copy");
        } 

    } else if (window.getSelection) {
        if(elt.nodeName.toLowerCase() === "input"){
            document.getElementById(containerid).select();
            document.execCommand("copy");
        }else{
            var range_ = document.createRange();
            range_.selectNode(document.getElementById(containerid));
            window.getSelection().removeAllRanges();
            window.getSelection().addRange(range_);
            document.execCommand("copy");
    }
    }
}
</script>
<center><p></p>
<button onClick="copym()">Copy Voucher!</button>
<script>
function copym(){
  copyer("hm");
}
</script>
<table id="hm">
```

### Pada kolom row isikan kode atau script berikut:

```markdown
<tr><td>"%u_actualProfileName%"</td></tr>
<tr><td>"%u_username%"</td></tr>
<tr><td>"%u_password%"</td></tr>
<tr><td>"%u_limitUptime%"</td></tr>
<tr><td>"%u_timeLeft%"</td></tr>
<tr><td>"%u_limitDownload%"</td></tr>
<tr><td>"%u_moneyPaid%"</td></tr>
```

### Pada kolom footer isikan kode atau script berikut:

```markdown
<tr><td></td></tr></table></center>
<script type="text/javascript">
var tables = document.getElementsByTagName('table');
var table = tables[tables.length - 1];
var rows = table.rows;
for(var i = 0, td; i < rows.length; i++){
td = document.createElement('td');
td.appendChild(document.createTextNode("[" + i + "]"));
rows[i].insertBefore(td, rows[i].firstChild);}
</script>
</body>
</html>
```

### Note:

Jangan mengubah kode atau script diatas karena dapat mengakibatkan proses cetak bermasalah!

Setelah semua benar simpan template. Selanjutanya generate voucher > copy kode voucher yang tampil dengan klik tombol "Copy Voucher!" > pastekan ke aplikasi iPrint > koneksikan bluetooth printer > klik proses > klik print > hasil print akan keluar ;)

iPrint Single hanya bisa cetak voucher 1 saja, dalam arti tidak bisa cetak voucher sekaligus banyak. Generate 1 voucher di userman untuk sekali cetak, dan jika ingin cetak lagi, generate lagi 1 voucher dan cetak, terus demikian.

iPrint Multiple hanya bisa cetak voucher maxsimal 5 saja. Generate 5 voucher atau lebih output cetak tetep 5. Tidak boleh generate voucher kurang dari 5 karena Aplikasi iPrint akan error!

Sekian, Semoga bermanfaat ;)
### Download [iPrint Free](https://play.google.com/store/apps/details?id=id.ioneservice.iprint.free)
