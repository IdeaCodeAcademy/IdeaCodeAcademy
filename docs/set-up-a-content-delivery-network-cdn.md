# Set up a content delivery network ( CDN )


   1. odoo ကို keycdn ဖြင့် ချိတ်ဆက်ရန်အတွက် ပထမဆုံး [keycdn.com](https://www.keycdn.com/) တွင် အကောင့်ဖွင့်ပါ။ 
   credit card မလိုပဲ အကောင့်စဖွင့်ဖွင့်ချင်း 1 credits ပေးပါသည်။

   2. ပြီးလျှင် အောက်ပါပုံအတိုင်း zone ထဲမှ add zone ကို နှိပ်ပါ။

      ![img.png](set-up-a-content-delivery-network-cdn%2Fimg.png)

   3. နောက်ထပ်အနေဖြင့် zone name နှင့် original url ကို ဖြည့်သွင်းပြီး save လိုက်ပါ။

      ![img_2.png](set-up-a-content-delivery-network-cdn%2Fimg_2.png)

   4. ယခုအချိန်တွင် မိမိတို့ ဖြည့်သွင်းလိုက်သော pulltest ဆိုသည့် zone ကို eploy ပြုလုပ်ရန် ဆယ်မိနစ်ခံကြာပါမည် ဆိုသည့်စာသားနှင့်အတး အောက်ပါအတိုင်း တွေ့ရပါမည်။
      deploy ပြီးဆုံးသည့်အခါတွင် ID Column ဘေးမှ status တွင် ဒုတိယ zone အတိုင်း အစိမ်းရောင်ဖြင့် ဖော်ပြပါလိမ့်မည်။ deploy ပြုလုပ်ပြီးလျှင် `Zone URL` ကို copy ကူးပါ။

      ![img_3.png](set-up-a-content-delivery-network-cdn%2Fimg_3.png)

   5. မိမိတို့၏ odoo server ကို CDN ဖြင့် ချိတ်ဆက်ရန်အတွက် CDN settings ကို on နိုင်ရန် developer mode ဖွင့်ထားရပါမည်။ လွယ်လွယ်ကူကူဖြစ်စေရန် url တွင် web နောက်မှ `?debug=1` ဆိုသည့် optional ကို အသုံးပြုပြီး ဖွင့်နိုင်ပါသည်။
      
      Original URL - 

      ``` 
      https://runbot.odoo.com/web#active_id=mail.box_inbox
      ```
      
      Debug On -
      
      ```
      https://runbot.odoo.com/web?debug=1#active_id=mail.box_inbox
      ```
      
   6. ဆက်လက်ပြီး website settings ထဲမှ Content Delivery Network (CDN) ကို on ပေးရပါမည်။ 
      
      ![img4.png](set-up-a-content-delivery-network-cdn%2Fimg4.png)
      
   7. အထက်ပါပုံတွင် CDN settings ကို on ထားပြီး CDN Base URL တွင် မိမိတို့၏ copy ကူးယူလာသော Zone URL ကို ရှေ့ဆုံးတွင် (//) နှင့် နောက်ဆုံးတွင် (/) တို့ကို ထည့်သွင်းပြီး အောက်ပါအတိုင်း ဖြည့်သွင်းရပါမည်။
      
      ```
      //pulltest-xxxxx.kxcdn.com/
      ```
   
   8. Zone URL ကို ဖြည့်သွင်းပြီးလျှင် မိမိတို့၏ browser ထဲမှ devtools တွင်  inspect ထောက်ပြီး network ထဲတွင် အောက်ပါအတိုင်း စစ်ဆေးနိုင်ပါသည်။

      ![img_4.png](set-up-a-content-delivery-network-cdn%2Fimg_4.png)
      
      အထက်ပါပုံတွင် မိမိတို့ server သို့ request လုပ်ရမည့်အစား CDN server သို့ request လုပ်သွားကြောင်း တွေ့နိုင်ပါသည်။