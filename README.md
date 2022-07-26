EMAIL GITHUB TIMELINE UPDATES

FEATURES:
->Probably the world's most popular code for sending email from PHP!
->Used by many open-source projects: WordPress, Drupal, 1CRM, SugarCRM, Yii, Joomla! and many more
->Integrated SMTP support – send without a local mail server
->Send emails with multiple To, CC, BCC and Reply-to addresses
->Multipart/alternative emails for mail clients that do not read HTML email
->Add attachments, including inline
->Support for UTF-8 content and 8bit, base64, binary, and quoted-printable encodings
->SMTP authentication with LOGIN, PLAIN, CRAM-MD5, and XOAUTH2 mechanisms over SMTPS and SMTP+STARTTLS transports
->Validates email addresses automatically
->Protects against header injection attacks
->Error messages in over 50 languages!
->DKIM and S/MIME signing support
->Compatible with PHP 5.5 and later, including PHP 8.1
->Namespaced to prevent name clashes


WHY YOU MIGHT NEED IT?
->Many PHP developers need to send email from their code. The only PHP function that supports this directly is mail(). However, it does not provide any assistance for making use of popular features such as encryption, authentication, HTML messages, and attachments.

->Formatting email correctly is surprisingly difficult. There are myriad overlapping (and conflicting) standards, requiring tight adherence to horribly complicated formatting and encoding rules – the vast majority of code that you'll find online that uses the mail() function directly is just plain wrong, if not unsafe!

->The PHP mail() function usually sends via a local mail server, typically fronted by a sendmail binary on Linux, BSD, and macOS platforms, however, Windows usually doesn't include a local mail server; PHPMailer's integrated SMTP client allows email sending on all platforms without needing a local mail server. Be aware though, that the mail() function should be avoided when possible; it's both faster and safer to use SMTP to localhost.

->Please don't be tempted to do it yourself – if you don't use PHPMailer, there are many other excellent libraries that you should look at before rolling your own. Try SwiftMailer , Laminas/Mail, ZetaComponents etc.

INSTALLING AND LOADING
PHPMailer is available on Packagist (using semantic versioning), and installation via Composer is the recommended way to install PHPMailer. Just add this line to your composer.json file:

"phpmailer/phpmailer": "^6.5"

or run
composer require phpmailer/phpmailer


A SIMPLE EXAMPLE:

<?php
//Import PHPMailer classes into the global namespace
//These must be at the top of your script, not inside a function
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\SMTP;
use PHPMailer\PHPMailer\Exception;

//Load Composer's autoloader
require 'vendor/autoload.php';

//Create an instance; passing `true` enables exceptions
$mail = new PHPMailer(true);

try {
    //Server settings
    $mail->SMTPDebug = SMTP::DEBUG_SERVER;                      //Enable verbose debug output
    $mail->isSMTP();                                            //Send using SMTP
    $mail->Host       = 'smtp.example.com';                     //Set the SMTP server to send through
    $mail->SMTPAuth   = true;                                   //Enable SMTP authentication
    $mail->Username   = 'user@example.com';                     //SMTP username
    $mail->Password   = 'secret';                               //SMTP password
    $mail->SMTPSecure = PHPMailer::ENCRYPTION_SMTPS;            //Enable implicit TLS encryption
    $mail->Port       = 465;                                    //TCP port to connect to; use 587 if you have set `SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS`
//Recipients
    $mail->setFrom('from@example.com', 'Mailer');
    $mail->addAddress('joe@example.net', 'Joe User');     //Add a recipient
    $mail->addAddress('ellen@example.com');               //Name is optional
    $mail->addReplyTo('info@example.com', 'Information');
    $mail->addCC('cc@example.com');
    $mail->addBCC('bcc@example.com');

    //Attachments
    $mail->addAttachment('/var/tmp/file.tar.gz');         //Add attachments
    $mail->addAttachment('/tmp/image.jpg', 'new.jpg');    //Optional name

    //Content
    $mail->isHTML(true);                                  //Set email format to HTML
    $mail->Subject = 'Here is the subject';
    $mail->Body    = 'This is the HTML message body <b>in bold!</b>';
    $mail->AltBody = 'This is the body in plain text for non-HTML mail clients';

    $mail->send();
    echo 'Message has been sent';
} catch (Exception $e) {
    echo "Message could not be sent. Mailer Error: {$mail->ErrorInfo}";
}

CODE:



<?php 
$int_a='1'; 
$int_b='-1'; 
$int_c='4'; 
$options=array( 
    'options'=>array( 
        'min_range'=>0, 
        'max_range'=>3, 
     ) 
); 
if (filter_var($int_a,FILTER_VARLIDATE_INT,$options!==FALSE){\ 
echo "Integer A '$int_a is considered valid (between 0 and 3).\n; 
} 
if (filter_var($int_b,FILTER_VARLIDATE_INT,$options!==FALSE){\ 
echo "Integer B '$int_b is considered valid (between 0 and 3).\n; 
} 
if (filter_var($int_c,FILTER_VARLIDATE_INT,$options!==FALSE){\ 
echo "Integer C '$int_c is considered valid (between 0 and 3).\n; 
} 
 
$options['options']['default']=1; 
if (($int_c=filter_var($int_c,FILTER_VARLIDATE_INT,$options!==FALSE){\ 
echo "Integer C '$int_c is considered valid (between 0 and 3).\n; 
} 
?>
