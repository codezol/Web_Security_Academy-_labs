## Lab: User role can be modified in user profile

**Goal**: Access Admin panel and delete user carlos account

**Solution**:

1- Test every functionality in the website and check all the responses you get.

2-when checking tha change email functonaliy using burp you can see that an object containing the new email, with other details, including the roleid.

3- send change email request to the repeater and add "roleid"=2 to the object containing the email.

4- after that the admin panel would be availble, access the admin panel and  delete user carlos account.