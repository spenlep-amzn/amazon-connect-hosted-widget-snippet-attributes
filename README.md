# Amazon Connect Hosted Widget Snippet Contact Attributes

> Note: if you have enabled [JWT security](https://docs.aws.amazon.com/connect/latest/adminguide/add-chat-to-website.html#confirm-and-copy-chat-widget-script) for your widget, you can also use this to pass encoded contact attributes

## Setup

Generate your Hosted Widget JavaScript snippet [[documentation](https://docs.aws.amazon.com/connect/latest/adminguide/add-chat-to-website.html)], and add the `amazon_connect('contactAttributes', {})` field

```diff
<script type="text/javascript">
  (function(w, d, x, id){
    s=d.createElement('script');
    s.src='https://asdf.cloudfront.net/amazon-connect-chat-interface-client.js';
    s.async=1;
    s.id=id;
    d.getElementsByTagName('head')[0].appendChild(s);
    w[x] =  w[x] || function() { (w[x].ac = w[x].ac || []).push(arguments) };
  })(window, document, 'amazon_connect', '<widgetId>');
  amazon_connect('styles', { iconType: 'CHAT_VOICE', openChat: { color: '#ffffff', backgroundColor: '#123456' }, closeChat: { color: '#ffffff', backgroundColor: '#123456'} });
  amazon_connect('snippetId', '<snippetId>');
  amazon_connect('supportedMessagingContentTypes', [ 'text/plain', 'text/markdown' ]);
   
+ amazon_connect('contactAttributes', { verificationCode: '999' }) //   <----- HERE
</script> 
```

## Usage

To access the attribute(s) in your contact flow, use the "Check Contact Attributes" Flow block [[documentation](https://docs.aws.amazon.com/connect/latest/adminguide/check-contact-attributes.html)

> NOTE: make sure to use **Namespace: User defined**

![image](https://github.com/spenlep-amzn/amazon-connect-hosted-widget-snippet-attributes/assets/150714337/1894a321-7b91-4be7-b4b4-6921c2c5a52b)
