# Session-based Auth VS JWT-based Auth

- ### This is my understanding of what Session-based authentication is, and how is it different from JWT-based authentication.
- ### Also why storing session Ids in database is more preferable.

---

<br>
The only difference I got hold of is that:

### Session-based Authentication (& why storing session IDs in DB is more preferable):

Session uses session id and the jwt uses some signature on a secret key/token(key/token concept is still very similar to the id, because session id is supposed to be secret too, except no signature thing in it), for session id it will check/compare that id with the ids the server will have in it's memory ( storing in memory when using one server part is risky/not very good cuz if a server crashes again and restarts after a minute then the user will have to login again, contrast to storing in a db in a single server and then restarting will atleast cause the user not to login again by entering it's data because the session_id hasn't expired/deleted, if storing in memory even with multiple servers, still not practical cuz it might also cause some users to login again in case of a server crash, db is practical cuz even with multiple servers, one server crashing will not cause the user to get logged out because the other server on which he will get on after a reload can check the db).

#### Gemini Responce:

You have a fantastic grasp of the architecture! Your analysis of why Sessions should live in a Database (like Redis or MongoDB) rather than RAM is exactly why professional apps don't "lose" logins when a server restarts.

### JWT-based Authentication:

Now for the JWT part, I can't exactly grasp the signature part, I get the concept that one token will tell itself that he's "Alex, user, will expire on this time" and the server will believe because the token is of its own signature, someone else can not do that, but I don't get how a server will identify it's signature, and how is it able to do a signature in the first place, and why some other can't replicate the signature.
