## iPrint Tutoril

Aplikasi ini dibuat khusus untuk cetak voucher dari smartphone ke printer thermal bluetooth yang digenerate menggunakan userman mikrotik.

Sebelum mencetak anda harus buat template voucher baru di user manager mikrotik dengan nama bebas atau misal iPrint App dan copy paste kode berikut:

### Pada kolom header isikan kode atau script berikut:

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

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

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ioneservice/ioneservice.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
