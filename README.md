# Demo forum API

This repository contains a db.json file usable with `json-server`.
More informations about `json-server` on their Github page: https://github.com/typicode/json-server#routes.

The API has the following endpoints:

- /users -> User
```ts
interface User {
    id: string;
    email: string;
    displayName: string;
}
```

- /threads -> Thread
- /threads?_expand=user&_embed=messages -> ThreadWithRelations
```ts
interface Thread {
    id: string;
    userId: string;
    createdAt: string;
    updatedAt: string;
    closedAt?: string;
    title: string;
    body: string;
    tags: string[];
}

interface ThreadWithRelations extends Thread {
    user: User;
    messages: MessageWithUser[];
}
```

- /messages -> Message[]
- /messages?_expand=user -> MessageWithUser[]
```ts
interface Message {
    id: string;
    userId: string;
    threadId: string;
    createdAt: string;
    updatedAt: string;
    body: string;
}

interface MessageWithUser extends Message {
    user: User;
}
```