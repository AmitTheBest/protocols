Outbox protocol implements a class that can be used to create and deliver messages.

``` php
$outbox = new \some\addon\Outbox([
    'key' = 'secret_api_key';
]);

$message = $outbox->newMessage('recipient_address');

$message['subject'] = 'Confirm your email';
$message['body'] = 'Click this link '.$link;

$message->send();
```

The protocol can be used to send out emails, text messages, internal inter-application notifications, push notifications and so on.

### Optional Features

#### Template Support

Some `Outbox` implementation may support local or remote templates. This allows developer to decorate mail messages by overriding the template. Message must support those two properties:

``` php
$message->template = 'email-confirm';
$message->tags['link'] = $link;
```

If templates are not supported or are not set-up then the ['body'] content will be delivered to the user.

#### Persistence

Outbox may want to store some local data:

``` php
$outbox = new Outbox(['db'=>$app->db, ... ]);
```

This can be used to store delivery status, out-outs or logs.





### List of add-ons that implement `Outbox`:

-   atk4/sendgrid - Send email messages through SendGrid.com
-   atk4/twillo - Send text messages through Twillo.com

## List of add-ons that rely on `Outbox`

-   atk4/login - Password reminder and User Registration



Note: if your add-on is not listed, please issue a PR.