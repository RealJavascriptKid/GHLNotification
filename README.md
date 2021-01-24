# GHLNotification
Temporary hack to display notification in GHL

## Instructions
- Switch to Agency View
- Goto Settings > Agency Settings
- Scroll All the way down to where it says "Custom Javascript"
- If there is any code already exists, make backup of it Just in Case and paste the following code after it
- If "Custom Javascript" text area is clear then just paste the provided code.


<pre>

<script type="text/javascript">

(function(){
    var  enable = true;
    var  message = "Refer a client to get $500 off"
    var  button = "Dismiss"

    
    function ghlNotification(){
       
        var notification = document.getElementById('saadNotif');
        if(notification)
            return;
        var html = '<div id="saadNotif" role="alert" class="alert --yellow" style="z-index: 99999;text-align: center;background-color: rgb(255 188 0);color: white;font-weight: bold;position: relative;display: block;top: 0;left: 0;"><div class="row"><div class="col" style="font-size: large;padding-top: 5px;">' + message + '</div><div class="col-2"><button id="saadsNotifBtn1" type="button" class="btn btn-secondary">' + button + '</button></div></div></div>';
        
        var wrapper = document.body 
        var notif = document.createElement('div')
        notif.innerHTML = html;	  
        var app = document.getElementById('app')
        wrapper.insertBefore(notif, app);
        setTimeout(function(){
            document.getElementById("saadsNotifBtn1").addEventListener("click", function() {
                document.getElementById('saadNotif').parentNode.remove()
            });
        },50)
    }
    if(enable)
        setTimeout(ghlNotification,1000)

})()

</script>

</pre>
