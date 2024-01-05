My first ctf report which has Arbitary File Upload Vulnerability.
1. Firstly, I visited the login page(login.html) 
2. Registered myself and then logged in.
3. Then, I tried to look into the page source but nothing came out to be useful for me.
4. After looking into every other pages , I found the upload feature in profile.html
![upload](https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/assets/101728835/7bec370b-f66c-41ac-b3a4-45711a84fe45)

5. Then i looked for the arbitary file upload feature.
6. First I uploaded a sample image, and checked its location on server using inspect element.
7. <img width="556" alt="inspect" src="https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/assets/101728835/e6d08eaa-0bb1-4156-b0c5-31f8494009b1">

8. It was time for a script..
  <?php 
  if(isset($_REQUEST['cmd'])){
      $cmd = ($_REQUEST['cmd']);
      system($cmd);
  }?>

9.  if we go to the non valid directory we can see the error is exposing that it is a Apache server and Apache server mostly uses php files.  <---Why I used php
10.  <img width="333" alt="whyphp" src="https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/assets/101728835/ffa298d8-bb16-43a5-8fe5-9b5357fef2a2">

11. Uploading my script. After a message "File Uploaded Successfully!" all I need to do is go to the uploaded image directory (assets/profPic/shelly.php) to make my script working.
12. We got the command execution!
![works](https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/assets/101728835/7d5e53b5-c00e-4312-8e44-2214b7a7b4d0)

![flag](https://github.com/AmanDekate1/SecurityBoat-2024-CTF-January-Challenge/assets/101728835/66d76444-ab19-4d49-85f3-9afeb25cbae1)


12. {Unrestr!cted_F!le_Upload_!s_Fun} 
