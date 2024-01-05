<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>Login-Beispiel</title>
    </head>
    <body>
        <h1>Login-Beispiel</h1>
        
<?php
$username = '';
$output_login_form = FALSE;
// Will sich jemand einloggen?
if (isset($_GET['login']) && $_GET['login']=='true') {
    // Stimmt Benutzername und Passwort überein?
    if(isset($_POST['username']) && $_POST['username']=='electrofreak' && isset($_POST['password']) && $_POST['password']=='123456') {
        echo '<h2>Herzlich Willkommen electrofreak!</h2>';
        echo '<p>Der Login hat funktioniert und nun kannst auf deine passwortgesch&uuml;tzen Daten zugreifen.</p>';
    } else {
        echo '<h2>Login Error!</h2>';
        echo '<p>Der Benutzername oder das Passwort ist falsch. Bitte &uuml;berpr&uuml;fe deine Eingaben.</p>';
        
        $output_login_form = TRUE;
        // Eingegebene Daten standardmäßig wieder in die Eingabefelder schreiben, damit der Benutzer nicht alles doppelt tippen muss.
        $username = htmlspecialchars($_POST['username']);
    }  
} else {
    $output_login_form = TRUE;
}

if ($output_login_form) {
    echo '<form action="./login.php?login=true" method="post">
            Benutzername: <input type="text" name="username" value="'.$username.'" /><br />
            Passwort: <input type="password" name="password" /><br />
            <input type="submit" value="Login">
        </form>';
}
?>

    </body>
</html>
