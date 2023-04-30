---
layout: post
title: Placeholder ...?
description: Oh... Such a strange place.
image: assets/images/aki_blossoms.png
nav-menu: true
---
<script src="/assets/js/aes.js"></script>
<div id="hints">
Like the title says, this is a placeholder. The layout required me to add another page but I'm still not sure what to put here. If you can think of something, tell me and I might add it. Otherwise, you might want to just go <a href="/landing.html">to the about me page</a> or <a href="/all_posts.html">to the blog</a>.
</div>

<script>
const alpha = "U2FsdGVkX1/i8upe8yVcMImDkoMTR5nkwCH2/XLtOdU7TEPXC/dtaRXY3+9gazvGGCU0Q4mi8whh8eHn0IZOR1oqQmXG5SErv6N9nYVQGbcEIDcin7tNnp4apI9UEH3MetilPzTldy/NOSGW0Cbr74SgsOCwINNvAvD1Gi3ig2I8Vy3W8c2HWIbxnk7aclnzw9lv3qzmLSXuIR+87foh6J/kfrfZ9UCmGQMh8WrPphuxq3IgJD1zLw+xfxv79bHcDturaOw3y/rqtG7Cf967VFjMWVzXBZ1R76qxR+wA6lbBjn+PzBPPWKDnMY8ld/20ruRHHu8sgHHK1HhNty2Rdy5knMTs6sPx0DymGplJ1bQ=";
const omega = "U2FsdGVkX1+vefL4n379/ISZR3vtJ7vgbJHaSD+8dZge1lOo+7LBxkmry32ssT4dqoOPfQu/5Wb/kKagzo8XgbaYdJwS/npsNT0aQ43MPpWBTV09vjWB8hE5lFFv68d/zQPICipS6ABNpbHDpUzaVKTJxhMfJb+6fAL/sSgBwSlwkbpzxzrAQNp3ZcPbM6CS8hHy+B3N372+srTlTuxp9Px2eeUo0MoMPGKW+W6qn2l3iqrw9JpM39C8PX2EsRYmD9Id6jK06xB/QmKO+/buaw==";
function magic(){
    if(window.location.hash) {
        var passphrase = window.location.hash;
        console.log(passphrase);
        const ciphertexts = [alpha, omega];
        for (const ciphertext of ciphertexts){
            try {
                const bytes = CryptoJS.AES.decrypt(ciphertext, passphrase);
                const cleartext = bytes.toString(CryptoJS.enc.Utf8);
                if (cleartext.length > 0){
                    console.log(cleartext);
                    var para = document.createElement("p");
                    txt = document.createTextNode(cleartext);
                    para.appendChild(txt);
                    document.getElementById("hints").replaceChildren(para);
                }
            } catch (error) {
                console.error(error);
            }
        }
    }
}
window.addEventListener("hashchange", (event) => {magic()});
magic();
</script>
