## iPrint Installation Tutorial

This application is made specifically for printing vouchers from smartphones to bluetooth thermal printers that are generated using Userman Mikrotik.

Download [iPrint Free](https://play.google.com/store/apps/details?id=id.my.iwifi.iprint.free) or download [iPrint Pro English](https://play.google.com/store/apps/details?id=id.my.iwifi.iprint.proen)

Before printing you have to create a new voucher template in the Mikrotik user manager. The process of making a voucher template is only once. Create a template with a free name or for example the iPrint App and copy and paste the following code:

### In the Header column, enter the following script:

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

### In the row column, fill in the following script:

```markdown
<tr><td>"%u_actualProfileName%"</td></tr>
<tr><td>"%u_username%"</td></tr>
<tr><td>"%u_password%"</td></tr>
<tr><td>"%u_limitUptime%"</td></tr>
<tr><td>"%u_timeLeft%"</td></tr>
<tr><td>"%u_limitDownload%"</td></tr>
<tr><td>"Rp %u_moneyPaid%"</td></tr>
```
#### Note:

To change the currency symbol, change the following script "Rp %u_moneyPaid%" replace the Rp symbol (symbol of the Indonesian currency) with the symbol of your country's currency. For example, your currency is dollars, write in the script "$ %u_moneyPaid%".

### In the footer column, enter the following script:

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

After all, save the template. Next, generate a voucher > copy the voucher code that appears by clicking the "Copy Voucher!" > Paste it into the iPrint application> connect to a bluetooth printer > click the process> click print > the print results will come out;)

iPrint Single can only print 1 voucher, meaning that you cannot print multiple vouchers at the same time. Generate 1 voucher on Userman for one print, and if you want to print again, generate 1 voucher again and print, continue to do so.

iPrint Multiple can only print a maximum of 5 vouchers. Generate 5 vouchers or more, but still 5 print output. You should not generate less than 5 vouchers because the iPrint application will have an error!

That's all, hopefully useful ;)

Download [iPrint Free](https://play.google.com/store/apps/details?id=id.my.iwifi.iprint.free) or download [iPrint Pro English](https://play.google.com/store/apps/details?id=id.my.iwifi.iprint.proen)
