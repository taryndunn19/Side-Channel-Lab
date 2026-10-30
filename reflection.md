# Description of the App

 In this assignment, I built a single-page browser app with three interactive tabs, with the help of AI. The first simulates a timing attack
 on an early-exit password check. The second shows how RSA's square-and-multiply leaks the private exponent through a
 power trace. The third compares the complexity of brute force with that of a side-channel attack.


# Reflection 
Before creating this app, I didn't truly understand how side-channel attacks work or how algorithms are involved. After creating the first tab, 
Timing Attack, I was able to visually see the process of a full attack and how differences in password verification time can be used to guess a 
password one character at a time. When a system compares a password character by character and finds an incorrect character, finding the correct one takes longer to process. I learned that this is how hackers can tell what characters are correct and which ones are incorrect, which was very interesting to me. 

In the Power Trace section of the app, I learned that hackers can observe a system's power consumption to figure out information about encryption keys.
Because the square-and-multiply algorithm performs different operations depending on what the bit in the exponent is, attackers are able to see those operations to help them crack the key. However, using the square-and-multiply-always technique can make the operations more consistent, which helps to prevent an attack. 

Lastly, the Complexity Comparison section of the app helped to show me how side-channel attacks are more effective than brute-force attacks. 
By using the sliders to change the Alphabet size, secret length, and timing samples per guess, I could see the difference of a side-channel vs brute-force attack. 
For example, when the alphabet size is 26, secret length is 11, and timing samples per guess was 100, the brute-force time ended up taking 4 hours, while the side-channel took less than one second. As a result, I learned that brute-force attacks require testing an increasing number of passwords, while a side-channel attack can potentially figure out a password with significantly less work. 


