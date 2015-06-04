## Painless emojis in your commit messages

Recently, while perusing some code on Github, I was saddened by the lack of emoji in my commit messages (and in everyone's commit messages, for that matter). Github provides a really nice facility for putting emoji in commit messages, but sometimes I just don't have the time to look up the right `<colon><name><colon>` magical keyboard combination to type that special text-friendly, Github-enhanced emoji. And so, as my commit history will unfortunately show, my commits lack a certain _zing_ and _pizzazz_ that emoji might help to bring.

I imagine many of you feel the same (or maybe I'm completely alone in this). Many of you, like I, worry and stress and wish you could add more whimsy to the dull task of writing commit messages.

Well, worry no more, because our long, national nightmare is over: I have solved our emoji problem. And all you have to do is run the following one-liner in each project you'd like to emojify:

```shell
# make sure you're in the project root, and then run:
$ curl https://raw.githubusercontent.com/peburrows/gitmoji/master/commit-msg > .git/hooks/commit-msg && chmod +x .git/hooks/commit-msg
```

What the above command will do is setup a git hook that will run every time you write a commit message. The hook will parse your message, looking for any words that can be replaced with an emoji and magically rewrite your commit to include those emoji.

So, a lazy commit message like:
"Don't put the dog in the house too soon"

Will magically become:
"Don't put the :dog: in the :house: too :soon:"

Also, because I know there are people out there who may occasionally want to be boring: if you throw a line that contains nothing but "no-emoji" in your commit message, parsing will stop there, and the rest of your message won't be any fun. But maybe no fun is what you want? For example:

```
Ah, jumping in my blue car!
no-emoji
My house was on fire, so I need to commit this quickly
```

Will turn into:

Ah, jumping in my :blue_car:!
My house was on fire, so I need to commit this quickly

You're welcome, America.
