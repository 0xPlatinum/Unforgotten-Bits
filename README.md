# Unforgotten-Bits


# The Challenge

![init](https://user-images.githubusercontent.com/98354876/228292782-d624553d-d310-473e-9ea2-547a507f6c52.png)

This was a 500 point challenge, and one of the most difficult forensics challenges ive done!
And so, lets jump into it. This is gonna be quite a journey

# Initial reconnaissance

We know that this is a disk partition from the description of the challenge, meaning we have a filesystem to explore! 
We can mount the disk to /mnt/t and begin.
Whenever I get disk partitions, I find the most useful place to start is the home directory. Entering the home directory of this new file system and we find a user named "yone". Yone has a decent amount of directories inside their home directory.

![image](https://user-images.githubusercontent.com/98354876/228298335-789790ea-b225-4c38-8768-8a6e7f306d69.png)

The one that sticks out to me as most interesting is the notes directory, since notes are usually related to important info (Passwords, usernames, missing security, etc).
Entering that directory, we get just three notes.

![image](https://user-images.githubusercontent.com/98354876/228299350-d38745e3-effe-4824-b49b-10d7601bd418.png)

Wow, all of this makes completely no sense. What the hell does any of this mean? Who takes notes like this? The third note is the most interesting, due to it *sounding* like a potential start to something important? Maybe a password, maybe a hidden file, or maybe its the beginning of a ritual to summon Cthulhu. Who knows. Lets just keep this in mind and continue exploring the other directories.

![image](https://user-images.githubusercontent.com/98354876/228302271-48572fc6-0fc5-407d-b37c-3e2274f164d3.png)

I decide to enter the "irclogs" directory, as a log directory might contain something important. Theres a lot of sub directories, and it would be useless to put in pictures. I decide to fully descend into the "01" directory. At the end, theres a single log file with what seems to be a chat log

![image](https://user-images.githubusercontent.com/98354876/228302984-ef0b8e8d-5137-401c-b236-8b08a3b14e11.png)

Here we have our main character Yone chatting it up with someone named "avidreader".
Yone tells us he is using the program steghide, as well as the password 'akalibardzyratrundle'. He also mentions the encryption being used, we might be able to decrypt something later with this information. Lets move on to some more logs!

# The Logging Directories

![image](https://user-images.githubusercontent.com/98354876/228303974-48b27469-cc84-43ca-b92b-5a128cdfabfc.png)

...They are all league of legends logs. After reading them all, the only thing I gained was a boredom. There was nothing useful, and nothing worth showing here.
Lets move on to even more logs! Woo! We love logs!

![image](https://user-images.githubusercontent.com/98354876/228304649-decd4901-5709-4ab7-915c-dc3719fbd7e2.png)

So just reading this, it would seem that "Light" is something illegal in this universe, maybe a drug? Our friend "avidreader" seems to have some panic attack after using this "light", so its possible.
However, nothing that stands out here either.
Since there are no more logs, we can move on to some other directories

Thats right, its time to explore the Mail directory!

# The Mail Directories

![image](https://user-images.githubusercontent.com/98354876/228305447-a9907128-071e-489f-9b50-04934d7af0bb.png)

Inside this directory, we can see three mail directories. A current one, a temp one, and a new one.

I decide to check out the tmp directory, only to find literally nothing inside of it. Zilch, zero, nada. So.. I move onto the "new" directory. 

![image](https://user-images.githubusercontent.com/98354876/228306637-88d18609-d773-4c62-8096-7f6b6b46fdd6.png)

A reminder from one Bob Bobberson (nice name) who claims himself to be the Azerite Master, who tells Sten Walker (yone) to delete all emails to prevent this "light" from falling into the wrong hands. This is just a weird email, but it does seem to support my working theory of light being a drug. Lets keep it in mind, and enter the "cur" directory.

![image](https://user-images.githubusercontent.com/98354876/228307251-7fac37d7-bafc-4ab0-918b-f064e40e14a7.png)

Aha! A bunch of emails in a similar format to the previous one, surely these will be useful and help us on our quest to uncover the light!

![image](https://user-images.githubusercontent.com/98354876/228307454-c052c688-c723-4256-a2d6-9ad5443b55f0.png)

...Its all spam emails. I've cut off the rest of them, as it would take up more space than necessary.

Sad.. Oh well! Lets move on to another directory. This time I chose to enter the hidden directory, lynx.
Entering this directory showed a single file, some browsing history

![image](https://user-images.githubusercontent.com/98354876/228308030-6e9c2904-db81-45c2-bb4a-39bb7fa3d249.png)

It appears our friends Yone was learning a bit of cryptography. he first searched for some number encodings, then checked out Church encoding, a colleges directory, and the Golden Ratio Base. Maybe he used one of them? We can note that down and continue our exploration!

Our final directory we havent checked out is "gallery"

# The Gallery Directory

![image](https://user-images.githubusercontent.com/98354876/228308597-078858f3-50d9-4316-a623-af0bedd8d9c6.png)

Four bmp files (Old image files basically). The images when opened dont seem important, just weird looking images. However, remember that conversation we got earlier about steghide? Why not try using it on the image files! Using steg hide on the image files 1, 2, and 3 with the password 'akalibardzyratrundle' (remember we got that from the conversation as well) and we get something from three of the files! We end up getting these three files, titled 
- dracula.txt.enc
- frankenstein.txt.enc
- les-mis.txt.enc

The fourth file, 7.bmp, actually failed to decode. So we ignored it for now and put it on the back of our mind.

When printing the contents of the three files, they gave garbage. Seems they are encoded after all. Well, no issue, we can try to use the AES information we recieved in that same conversation in an attempt to decode it! Now, Im no good with cryptography, I know nothing about it; However, my team does! My teammate SirSquibbins wrote a quick decryptor script (will be provided later if he approves) and decrypted the secret files! Aha! Surely, this must contain some hint somewhere, nobody would encode something for no reason!

![image](https://user-images.githubusercontent.com/98354876/228310363-ea199121-3906-4149-8e92-b284f9d997aa.png)

its.. its literally just the books. Its the books in their entirety, and nothing else. All three of them, books.

It was at this point I was stumped. I had zero clue what to do from here after getting those decrypted. However, Im glad I wasnt alone! Me and my team decided to dig into that weird third note, and thats when I was informed by another one of my teammates, Flipout50, that these were actually League of Legends characters names combined! "yasuoaatrox" or "yasuo and aatrox"! 

Question becomes.. what the hell do we do with this information? yea so what, yone combined two LoL names, what does that do for us?
It was at this point me and my team decided that the 7.bmp file is likely our end goal, and we clearly need a new password for it.
We tried all words in the "notes" files, and nothing worked. We tried the same password, keywords from the chat logs, etc, and it all failed.

# Desperation

This was the point I got desparate and did the thing all desperate people do. I ran "strings" on the disk image and grepped for "password"
And... it worked! I actually found something!

![image](https://user-images.githubusercontent.com/98354876/228312502-59b9e2f9-0ef0-4075-b4f1-21555d69afbd.png)

Looks like an email! But thats weird, because we *searched* the emails, and this wasnt there? Maybe it was deleted but kept in the memory? I dont know, and i dont care; we found **something**. After getting this I decided to grep for "> subject: Re: Enlightened passwords" and get 20 lines before and after, so we can extract the full email exchange.

![image](https://user-images.githubusercontent.com/98354876/228313331-2dcc22be-dac9-4435-bcec-b003b6657bb5.png)

Not only do we find the full conversation, but we actually *see* the command trace of yone deleting this email! Thats why we couldnt find it!
Now reading the email, we are told that the most important password is created using the xkcd comic (https://xkcd.com/936/). This comic suggests getting four random things you know, and combine them into some sentence or such to remember it. 

It was at this point my team remembered that intial third note, and began to think that those two LoL champion names are the first two parts of the password!

![image](https://user-images.githubusercontent.com/98354876/228313888-bcb97f5a-6f7a-44ca-9bb6-131e963c7b60.png)


Flipout50 created a wordlist of all the champion names, and SirSquibbins made the bruteforcer!
Finally, now we can get this hidden data out of the bmp!

![image](https://user-images.githubusercontent.com/98354876/228314436-61f3eead-ee07-4203-8882-19e500be584e.png)

We get a ledger!
Except its encrypted data and our old decryptor fails. We have no other clear leads, we used the third note, the gallery images, the emails,  and the irc logs.

The only things we havent used at this point was the browsing history, and note 1 and 2.

This.. This final step is where we got stuck for many days.

After not getting a step further for a while, i made this meme

![image](https://user-images.githubusercontent.com/98354876/228315252-0fd2b0bb-8f89-4d3a-ba1a-325b909a1831.png)

to help calm our insanity and hair pulling.

# Digging through sand until we find treasure.

And then, one Thursday afternoon, I found something.
I had decided out of desperation to open the disk image in Sublime text and read everything ***manually***. Maybe strings got rid of something it didnt consider a string, who knows. Eventually, I had found where the notes were stored in the image viewing it from Sublime. Except.. something else was there as well

![image](https://user-images.githubusercontent.com/98354876/228315783-b143426c-e296-4ba1-bc7f-663dd4faee06.png)

There was some weird string of binary we had not seen before, in between the first and second notes. I instantly threw it into Cyberchef, only to get garbage back: No easy win there.

After some back and fourth discussion with SirSquibbins, Flipout50, me, and another team member Quest, we finally wrapped back around to the search history.

![image](https://user-images.githubusercontent.com/98354876/228316724-f9fe65a0-f949-44f9-bc93-ca08f91d168c.png)

SirSquibbins thought maybe we reverse the binary, starting from the golden ratio base, since that seems to match up with our binary strings (Atleast it *looks* like it).

Three days go by, after testing and testing and testing, with no results.

# Persistance is the key to success

One cool, calm, dark, afternoon. 

At 9:15pm on a Monday, Flipout obtained something. He had began decoding the binary bits, and managed to extract "salt=".

![image](https://user-images.githubusercontent.com/98354876/228317612-afa3beea-7105-4d6b-b4bd-acac5485acf6.png)

And finally... We had obtained another encryptor.
The flag was obtained by decrypting the ledger.enc with the new information we have, and we were finally finished.

GGs, Pico, a tough challenge, but we finally solved it. Just took us a bit, yknow?
