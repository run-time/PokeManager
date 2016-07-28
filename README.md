# Pokemon Manager for Pokemon Go

This was a project that I decided to throw together to fill a niche that hasn't yet been filled. I won't be actively updating this, and there is not much error handling, so **use with care**.

This is essentially just a modified demo of the [Python API for Pokemon Go available here](https://github.com/rubenvereecken/pokemongo-api), so give them the credit. Also, anything that will
work for that API will work here as well.

I just tweaked it to do what I want. Feel free to reuse this. I just wanted something until someone made something better.

If you have any suggestions, and I like them, I will be happy to look into it - but please don't expect me to be as active as the other developments going on.

**Disclaimer**: This is built using an unofficial API. ***All*** of the unofficial APIs stand a risk of getting you banned. So use with caution!

## What does it do?

It does 4 things:

1.  Allows you to view all your Pokemon and their stats (CP and IVs)
  1.  It also groups / sorts alphabetically, and then by IV%
  2.  It also colour codes based on the IV% (Green for >75, Yellow for >50, White for the rest)
2.  Allows you to view how many of each Pokemon you have, as well as how many candies you have for that Pokemon
  1.  It also shows how many you can evolve
  2.  At the bottom of the list it will show you how many "base" Pokemon you can evolve. That is, those Pokemon that are tier 1 evolves only.
3.  Allows you to mass transfer Pokemon
  1.  You can set "safe" limits of IV% and CP. This will not transfer anything that is above either of those levels.
  2.  It will show you how many of that Pokemon is "safe" to transfer, along with their stats
  3.  It will ask how many of the "safe" Pokemon you want to transfer.
  4.  It then shows you the pokemon that will be transferred, and their stats. And asks to confirm if you want to transfer them.
  5.  If specifying certain numbers (lower than the total "safe" Pokemon) it will always transfer the lowest IV% Pokemon first
4.  Allows you to rename your Pokemon to include their IVs
  1.  Currently it will rename your Pokemon to IV%-ATK/DEF/STA. There is a char limit of 12, so no room for anything else. I chose IV first because you can order by name, thus getting highest IV.
  2.  It allows you to set an IV% limit so it will only rename those Pokemon that are above that limit

## Important Info / Updates

* Pokemon names must be in ALL CAPITALS. It uses the API names (easy to look up)
* You can now specify ALL to transfer ALL Pokemon below the IV and CP thresholds
* The release and rename functions will take a long time if there are a lot of pokemon. This is to help reduce bot detection by adding delays to requests

## How to run it

#### OSX Instructions

After you clone this repo, you'll want to navigate into your project.

```
$ git clone https://github.com/tsaiDavid/PokeManager.git
$ cd PokeManager
```

Now, you'll need to install the Python dependencies using pip. If you're on OSX and haven't run pip before, please look into install Python via "Homebrew":

```
# Optional, potentially needed if first time user.
$ brew install python; brew linkapps python;

$ pip install -r requirements.txt

```
If you're denied due to permissions issues, simply run the `pip install` command mentioned above, but with a leading `sudo`.

Now that you've taken care of the requirements, let's handle the changes you need to make to the `run.example.sh` you see in the repo. We'll start by duplicating the file and renaming it to `run.sh` (this can be changed at your discretion).

```
$ cp run.example.sh run.sh
```

Open your newly created `run.sh` file and replace the username, login, and location with your appropriate details, be sure to save the file. Now, let's run the script.

```
$ sh run.sh
```

##### NOTES:

* If at any time you need to exit the program simply hit: <kbd>ctrl</kbd> + <kbd>c</kbd>
* My version of this code has made a few simple changes in order to speed up the renaming process - it keeps the "randomness" of the server calls being made and each rename will range between 0.15s - 0.25s. If you're having trouble with this, please let me know.

#### Original Windows Instructions

Make sure you have Python and the requirements installed. If you don't have Python installed, search how to do it. **Use Version 2.7.x**. Make sure you have pip as well.

To install the requirements, open a CMD window in the root folder and run:

```pip install -r requirements.txt```

If this gives you an error about not finding pip, please search how to install Python and pip (and make sure python is added to your PATH).

In the root directory there is a file called **PokeManager.bat**. Open it with your favourite editor and you should see this:

```python ".\pogo\demo.py" -a google -u "user@gmail.com" -p "password" -l "lat, long"```

Replace the email, password, and coordinates (coordinates can also be a location that Google recognises)

Run PokeManager.bat. There should be a menu presented to you. Follow along. Don't try to break it - you will.

If you want to use PTC, change `-a google` to `-a ptc`

**NOTE:** I don't know if this API supports 2FA. If you have 2FA and it gives you Auth errors, set up an [App Password](https://security.google.com/settings/security/apppasswords).

## Screenshots

### Main Menu

![Main Menu](/media/main_menu2.png?raw=true "Main Menu")

### Viewing Pokemon

![Viewing Pokemon](/media/view_pokemon2.png?raw=true "View Pokemon")

### Viewing Totals of Pokemon

![Counting Pokemon](/media/count_pokemon2.png?raw=true "Count Pokemon")

### Transferring Pokemon

![Transferring Pokemon](/media/transfer_pokemon2.png?raw=true "Transfer Pokemon")

### Renaming Pokemon

![Renaming Pokemon](/media/rename_pokemon.png?raw=true "Rename Pokemon")
