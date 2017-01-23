# Inhibitors

Inhibitors run on messages that are confirmed to be a bot command - the prefix has been detected and the command has found. They can be used to *stop* a command from running depending on circumstances. 

Default inhibitors include checking if a user has permissions, whether other pieces are missing, the bot doesn't have permission to execute a command, etc. 