---
title: Rails Action Mailer Configuration
date: 2021-06-21
tags: ['action mailer', 'Ruby On Rails', 'ActionMailer', 'gmail']
---

# Rails Action Mailer Configuration

![action mailer](/images/rails-action-mailer-configuration.png)

### Action Mailer overview

Rails has a wonderful built-in mailing system called Action Mailer, which allows us to send email
from our application as long as we have a mailer model. Mailers are actually a lot like controllers:
they have their own app/mailers directory, and each mailer has its own associated view as well. Each
mailer also inherits from ActionMailer::Base, and just like controllers, can be generated really
easily.

This tutorial explains how to configure Ruby on Rails in the development environment toward sending
emails via Ruby on Rails Action Mailer integrated with the most popular email providers Gmail &
SendGrid.

Let’s take it step by step, first we need to do a bit of configuration, we are going to send emails
from the developement enviroment.

## ActionMailer Gmail Confiruation

In order to use Action Mail with Gmail, the best solution that does not violate your other security
such as 2-step certification is using
[app Password](https://support.google.com/accounts/answer/185833)

\*\* Open your [Account Security Settings](https://myaccount.google.com/security)

![Alt google-app-passwords](/images/action-mailer-config-1.png)

- Navigate to App Password

![Alt google-app-passwords](/images/action-mailer-config-2.png)

On the App Password page, select “Mail” app, and “Other” device, now we provide the name of ruby on
Rail application. Then click “Generate”.

![Alt text](/images/action-mailer-config-3.png)

Copy your App password from the yellow Box.

# ActionMailer Rails Confiruation

Ruby doesn’t require any additional gems to be installed, as it’s just a simple smtp setting, we
just need to configure the setup by adding the following code into our file development.rb so that
the Action Mailer and mailcatcher will be setup properly.

```yaml
  config.action_mailer.delivery_method = :smtp
  config.action_mailer.smtp_settings = {
    address:              'smtp.gmail.com',
    port:                 587,
    domain:               'example.com',
    user_name:            'youremail@gmail.com',
    password:             'xxxunxtbxyvmzxxx',
    authentication:       'plain',
    enable_starttls_auto: true,
    open_timeout:         5,
    read_timeout:         5
  }
```

for mote informaition refer to
[Action Mail Confiruation for Gmail.](https://guides.rubyonrails.org/action_mailer_basics.html#action-mailer-configuration-for-gmail)

### To start, we’ll use Rails to generate a mailer:

## Creating a Mailer

So the first thing we need to do is to create a new Mailer. To do this we can use the Rails
generator:

```terminal
  rails generate mailer UserMailer welcome_message
     create  app/mailers/user_mailer.rb
     invoke  erb
     create    app/views/user_mailer
     create    app/views/user_mailer/welcome_message.text.erb
     create    app/views/user_mailer/welcome_message.html.erb
```

Running this command in the terminal generates a few different files for us. We now have an
app/mailers directory, with an user_mailer.rb and application_mailer.rb file.

```ruby
  class ApplicationMailer < ActionMailer::Base
    default from: "from@example.com"
    layout "mailer"
  end
```

Theapplication_mailer.rb is the base class that all other mailers are going to inhert from, we
notice it inherts from ActionMailer::Base and the first thing it does it cause the default method
default from: "from@example.com" and passes some options, these option will be applied to all of our
email by default because it's defined up here in the base class. The from option is the email
address you want to use as the sender of the email.

```ruby
  class UserMailer < ApplicationMailer
    def welcome_message
        @greeting = "Hi"
        mail to: "to@example.org", subject: 'Account registration'
    end
  end
```

It also generated this UserMailer, notice that the user_mailer.rb inherts from the
ApplicationMailer.

Now this mailer classes works similarlly to rails controllers, they inherts from the common base
class, in this case “ApplicationMailer”. Thet also has a method inside of him, notice that this
method correspond to the name we gave in the command line “welcome_message” , and those methods are
similiar to controller actions, but instead of generating an HTML response, “mailer” method generate
an “email”.

So this welcome_message is goning to generate the email we want. we also see that step down method
includes this “@greeting” instance variable, an instance variables define inside of welcome_message
method are accessabile in view templates just like we would expect with the controller action.

And the last line of these mailer methods must call this mail method to accualty create a mail
message a return it. now you notice we can also pass option to this method, in this case we have the
option to:, this the person we want to send the email to.

To create that email, the mail method is goning to render some email template, now the generator
went ahead and created 2 email templates for us to render that new message. and those templates are
over in:

```tree
  App
  |- Views
  |- user_mail
  |- welcome_message.html.erb
  |- welcome_message.text.erb
```

notice that the name of the file includes the name of the mailer method, welcome_message.html.erb
that generates an HTML email and welcome_message.text.erb that generates a plain text email.

If we take look at the HTML template, what we see it looks just like any other view template.

It’s a good practice to send both plain text and HTML email and let the email client decide which
one to display, and the action mailer does all the heavy lifting for us because we have 2 views
templates with the same name but different content types ebedded in their file names, both templates
will get rendered and sent out in one multi-part email.

Let’s go ahead and setup a user login with our welcome_message method, so our users_controller.rb
looks like:

```ruby
def create
 @user = User.new(signup_params)
 if @user.save!
   session[:user_id] = @user.id
   UserMailer.with(user: current_user).welcome_msg.deliver_now
   render json: @user, status: :created
 end
end
```

It would be handy to change our template so that it generates an email content we want.

```ruby
<h1>Welcome to www.example.com, <%= @user.name %></h1>
   <p>You have successfully signed up to www.example.com</p>
   <p>Your email address is : <%= @user.email%></p>
   <p>Your user name is : <%= @user.user_name%></p>
<p>Thanks for joining and have a great day!</p>
```

[link on medium](https://medium.com/@akladyous/ruby-on-rails-action-mailer-configuration-6d0cfc00b871)

##### Conclusion

It doesn’t really matter if you are building a consumer or business application, you’re going to
need to send emails to your users as some point.

[Unlock Further Insights by Sharing 🔗](https://medium.com/@akladyous/ruby-on-rails-action-mailer-configuration-6d0cfc00b871)

Thank you for reading! ❤️
