# GHLNotification
Temporary hack to display notification in GHL.

# DISCLAIMER
I won't be responsible for any damage it caused. I am sharing it just for the benefit of others. I am myself going to use the same code for my own GHL Agency. Also I am Developer so I understand playing with code.

Also this shouldn't be taken as primary solution. This is temporary hack to achieve what you want. I would definately use the official solution if/when provided by GHL.



## Instructions
- Switch to Agency View
- Goto Settings > Agency Settings
- Scroll All the way down to where it says "Custom Javascript"
- If there is any code already exists, make backup of it Just in Case and paste the following code after it
- If "Custom Javascript" text area is clear then just paste the provided code.


 ```html


<script type="text/javascript">

(function(){
    var  enable = true
    var  message = "Refer a client to get $500 off"
    var  proceedButton = "Proceed"
    var  dismissButton = "Dismiss"
    var  proceedButtonURL = "https://google.com"
    var  openURL_In_New_Tab = true

    
    
    function ghlNotification(){
       
        var notification = document.getElementById('saadNotif');
        if(notification)
            return;
        var buttonsHtml = '',col_class = 'col-2';

        if(proceedButton && proceedButtonURL){
            var targetBlank = (openURL_In_New_Tab)?'target="_blank"':'';

            buttonsHtml += '<a id="saadNotifProceedBtn" href="' + proceedButtonURL + '" ' + targetBlank + ' class="btn btn btn-success" style="margin-right: 11px;">' + proceedButton + '</a>'
            if(dismissButton)
                col_class = 'col-3'
        }

        if(dismissButton){
            buttonsHtml += '<button id="saadNotifDismissBtn" type="button" class="btn btn-secondary">' + dismissButton + '</button>'
            if(proceedButton)
                col_class = 'col-3'
        }

        var html = '<div id="saadNotif" role="alert" class="alert --yellow" style="z-index: 99999;text-align: center;background-color: rgb(255 188 0);color: white;font-weight: bold;position: fixed;display: block;top: 0;left: 0;width: 100%;"><div class="row"><div class="col" style="font-size: large;padding-top: 5px;">' + message + '</div><div class="' + col_class + '">' + buttonsHtml + '</div></div></div>';
        
        var wrapper = document.body 
        var notif = document.createElement('div')
        notif.innerHTML = html;	  
        var app = document.getElementById('app')
        wrapper.insertBefore(notif, app);
        setTimeout(function(){

            if(dismissButton){
                document.getElementById("saadNotifDismissBtn").addEventListener("click", function() {
                    document.getElementById('saadNotif').parentNode.remove()
                });
            }           

        },50)
    }
    if(enable)
        setTimeout(ghlNotification,1000)

})()

</script>

 ```
