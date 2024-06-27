### Register SSL certificate
An SSL certificate will help to encrpty communication between visitors and websites It ensures that the data transmitted between the user's browser 
and the website's server remains confidential and cannot be intercepted or tampered with by unauthorized parties,this is also known as encryption in transit.
<br>
![SSL1](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/0fb2c4c3-a5d6-47c3-bf8c-6ff0bdb3b0e4)

AWS certificate manager(ACM) is service managed by AWS,we will use it to register SSL and will use the certificate to encrypt the communication between the web browser and our web servers
<br>
To access the ACM,on your management console navigate to the search bar and type certificate manager
<br>
When the certificate manager page opens click on "Request a certificate" as seen above
<br>

![SSL2](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/73afc54a-be68-4c22-b1a6-45986020dad2)

When the request certificate page opens,under certificate type choose "request a public certificate" as seen above then click Next
<br>

![SSL3](https://github.com/AdventureLouis/Wordpress_Deployment_To_AWS_2/assets/161846069/dc1ceb27-1957-4d31-b11f-a795dfcda0cd)

This part requires you have a domain,so I already transferred my domain name from my previous AWS account to my new AWS account
Under "Fully qualified domain name" type your domain name and click "Add another certificate" and this time type "*.your domain name" 1.e *.loalab.org as seen above
<br>
Under  validation method choose DNS validation
<br>
Under key algorithm choose RSA 2048 and click request
