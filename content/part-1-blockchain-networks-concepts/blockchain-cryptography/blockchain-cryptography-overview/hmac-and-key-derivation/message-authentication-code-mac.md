# Message Authentication Code (MAC)

**M**essage **A**uthentication **C**ode is cryptographic code, calculated by given **key** and given **message**:
```
auth_code = MAC(key, msg)
```
Typically, it behaves **like a hash function**: a minor change in the message or in the key results to totally different **MAC value**. Also, it should be practically infeasible to change the key or the message and get the same **MAC value**.

The MAC code is **digital authenticity code**, like a **digital signature**, but with **pre-shared key**. We shall learn more about digital signing and digital signatures later.

# When we Need MAC Codes?

A sample scenario for using MAC codes is like this:
 - Two parties exchange somehow a certain secret **MAC key** (pre-shared **key**).
 - We receive a **msg** + **auth_code** from somewhere (e.g. from Internet, from the blockchain, or from email message).
 - We want to be sure that the **msg** is **not tampered**, which means that both the **key** and **msg** are correct and match the MAC code.
 - In case of **tampered message**, the MAC code will be incorrect.

![](/assets/MAC-message-authentication-code.png)

## Encrypt / Decrypt Messages using MAC

Another scenario to use **MAC codes **is when we **encrypt a message** and we want to be sure the **decryption password is correct**.
 - First, we **derive a key **from the password. We can use this key for the MAC calculation algorithm (directly or hashed for better security).
 - Next, we **encrypt the message** using the derived key and store the ciphertext in the output.
 - Finally, we calculate the **MAC code** using the derived key and the original message and we append it to the output.
 
When we **decrypt the encrypted message** (ciphertext + MAC), we proceed as follows:
 - First, we **derive a key **from the password, entered by the user. It might be the correct password or wrong. We shall find out later.
 - Next, we **decrypt the message** using the derived key. It might be the original message or incorrect message (depends on the password entered).
 - Finally, we calculate a **MAC code** using the derived key + the decrypted message.
   - If the calculated MAC code matches the MAC code in the encrypted message, the **password is correct**.
   - Otherwise, it will be proven that the decrypted message is not the original message and this means that the **password is incorrect**
   
The MAC is stored along with the ciphertext and it **does not reveal **the password or the original message. Storing the MAC code, visible to anyone is safe, and after decryption, we know whether the message is the original one or not (wrong password).

## MAC-Based Pseudo-Random Generator

Another application of MAC codes is for **pseudo-random generator** functions. We can start from certain **salt** (constant number or the current date and time or some other randomness) and some **seed** number (last random number generated, e.g. **0**). We can calculate the **next_seed** as follows:
```
next_seed = MAC(salt, seed)
```
This **next pseudo-random number** is "randomly changes" after each calculation of the above formula and we can use it to generate the next random number in certain range.
