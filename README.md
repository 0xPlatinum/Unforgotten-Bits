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

Wow, all of this makes complete...ly no sense. What the hell does any of this mean? Who takes notes like this? The third note is the most interesting, due to it *sounding* like a potential start to something important? Maybe a password, maybe a hidden file, or maybe its the beginning of a ritual to summon Cthulhu. Who knows. Lets just keep this in mind and continue exploring the other directories.

![image](https://user-images.githubusercontent.com/98354876/228302271-48572fc6-0fc5-407d-b37c-3e2274f164d3.png)

I decide to enter the "irclogs" directory, as a log directory might contain something important. Theres a lot of sub directories, and it would be useless to put in pictures. I decide to fully descend into the "01" directory. At the end, theres a single log file with what seems to be a chat log

![image](https://user-images.githubusercontent.com/98354876/228302984-ef0b8e8d-5137-401c-b236-8b08a3b14e11.png)

Here we have our main character Yone chatting it up with someone named "avidreader".
Yone tells us he is using the program steghide, as well as the password 'akalibardzyratrundle'. He also mentions the encryption being used, we might be able to decrypt something later with this information. Lets move on to some more logs!

![image](https://user-images.githubusercontent.com/98354876/228303974-48b27469-cc84-43ca-b92b-5a128cdfabfc.png)

...They are all league of legends logs. After reading them all, the only thing I gained was a boredom. There was nothing useful, and nothing worth showing here.
Lets move on to even more logs! Woo! We love logs!

![image](https://user-images.githubusercontent.com/98354876/228304649-decd4901-5709-4ab7-915c-dc3719fbd7e2.png)

So just reading this, it would seem that "Light" is something illegal in this universe, maybe a drug? Our friend "avidreader" seems to have some panic attack after using this "light", so its possible.
However, nothing that stands out here either.
Since there are no more logs, we can move on to some other directories

Thats right, its time to explore the Mail directory!

![image](https://user-images.githubusercontent.com/98354876/228305447-a9907128-071e-489f-9b50-04934d7af0bb.png)

Inside this directory, we can see three mail directories. A current one, a temp one, and a new one.
