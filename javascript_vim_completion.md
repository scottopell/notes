# JS Code Completion in Vim

You can get keyword/ID based completion with standard YouCompleteMe or omnicomplete,
but for completion that takes into account the context of the file and the libraries you're working with,
you need more.

That more is [tern](http://ternjs.net/).

- Install YCM with tern support. Here is what I use because I also want tab completion for C-family languages
  `cd ~/.vim/bundle/YouCompleteMe && ./install.py --clang-completer --tern-completer`
- create a `.tern-project` file in your current project with your current settings loaded.
- Restart vim from the directory with `.tern-project`

An example "base" tern-project file I've been using is

```
{
  "libs": ["browser", "jquery"],
  "plugins": {
    "node": {}
  }
}
```

The "node" plugin **should** load any dependencies from package.json, however this doesn't neccessarily get you completion
for those libraries.

There is an `ecmaVersion` field you can add and the default value is `6`, which the docs note should be fine for es5 as well.
