The items in the json file fit nicely into this es6 class:


```ecmascript 6
class Post {
    constructor(item) {
        this.number = item.number;
        this.timestamp = item.timestamp;
        this.board = item.board;
        this.site = item.site; // '4chan' or '8chan'
        this.threadId = item.threadId;
        this.text = item.text;// nullable
        this.subject = item.subject;// nullable
        this.name = item.name;// nullable
        this.trip = item.trip;// nullable
        this.email = item.email;// nullable
        this.isQ = item.isQ;// nullable
        this.images = item.images;// nullable
        this.references = item.references; // nullable, an array of ids
    }

    get moment() {
        return moment(this.timestamp * 1000)
    }

    get source() {
        return this.site + '_' + this.board
    }

    get id() {
        return this.source + '_' + this.number
    }

    get link() {
        return this.site === '4chan' ? `https://archive.4plebs.org/${this.board}/thread/${this.threadId}/#${this.number}` :
            `https://8ch.net/${this.board}/res/${this.threadId}.html#${this.number}`;
    }
}
```
