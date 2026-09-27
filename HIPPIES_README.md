Thanks for opening the Readme! Here are my notes on making this mod.

## I wanna make a personality like this! ##
I figured you were going to ask that. Here's what you need to do.

1- Start with a script. No, not a code script (unless you want to do that), I'm talking about an actual script for character dialogue. How does this empire want to be perceived by the galaxy? Think very carefully about the kind of image you want to project here. 
! Remember, if their civics, ethics, or government form chanegs, depending on how you key their personality, it could obliterate all the dialogue you have planned. If you can, try to key the personality requirements to something that can't change later in the game, like the Chosen civic, or a species portrait.
! Don't try to skip out on work and only write a few lines. The way that the diplo-phrases files I wrote work, you'll have to deal with replacing EVERYTHING. You can always key default phrases in vanilla $using_dollar_quotes_like_this$, but you do still have to make a MYPERSONALITY_GREETING_01 statement. 
! Relax, and take your time. Writing is hard work. And it's worth it to do it on your own, with your own brain. If you rush it, it'll come out like crap.

2- Decide how you want this personality to behave.
As you've noticed, the Hippies and both of the Pirates have specific behaviors related to their personalities. That back-end functionality is difficult to maintain because it requires overwriting code in blocks frequently used by other mods. If you don't stay on top of things like updates and patches, you could end up breaking a lot of things without meaning to. The only reason I touch as many files as I do is because I'm one of the maintainers of E&CC. I know what changes are coming down the line, so I can prepare for them.
! Avoid editing load-bearing files like ethics.txt or civics.txt unless you know you can maintain this mod, know what changes are happening, or otherwise know what you're doing.

3- All hail the almight, all-wise KISS... Keep It Simple, Stupid.
This is a rule I need to remember to follow more often. When you keep a task simple, you're setting yourself up for success. The more complicated it becomes, the more likely it is to break. As awesome as it would be to have this empire have a specific catch-phrase that they say only with empires that have this specific civic after they've developed this specific technology, that's involving a lot of conditions, triggers, and otherwise iffy variables that your players might not even see. Ask me how often I've had players encounter Hippies that have successfully made the Planetary Shielder colossus.

4- The files you need to write.
Here's all the stuff you need to get your own Expressive personality working:
 - common/personalities/mypersonality_personalities.txt
 - common/opinion_modifiers/mypersonality_personality_opinions.txt
 - common/diplo_phrases/mypersonality_diplo_phrases.txt
 - common/scripted_triggers/mypersonality_scripted_triggers.txt (more later)
 - localisation/klingon/mypersonality_l_klingon.yml

If you're using my files to make your personality, you need to add your own entry to the is_special_personality trigger.

    is_special_personality = {
	    OR = {
		    has_ai_personality = peaceful_counterculture
		    has_ai_personality = mirthful_bandits
		    has_ai_personality = cunning_raiders
		    #has_ai_personality = mega_union
            has_ai_personality = my_expressive_personality
	    }
    }

What this does is it tells the overwritten diplo-phrases files that your personality has its own dialogue, and it should ignore it when presenting dialogue in the diplomacy window. When you do this, you're going to have to make sure that you have a proper dialogue entry for every article in 00_diplo_phrases_02.txt, 00_diplo_phrases_nomads.txt, and (if they are or can ever be a megacorporation) 00_corp_greeting_overwrites.txt.

Everything after that is localisation. And trust me, it's a hell of a lot harder than it looks. If you're localizing in English (my native language), you have it pretty easy. If you're localizing in other languages, you may have to look for extra help to make sure that your super-cool AI personality is using good grammar.

For any localisation, you need a text file that is saved with a '.yml' extension. YAML is short for Yet Another Markup Language, and it's what the Clausewitz engine uses to read loc files. You can write one in any text editor that isn't Microsoft Word or LibreOffice Writer. But, you need to make sure that you're saving the file with UTF-8-BOM encoding, which is short for 'Universal Text Format 8, with Byte-Order Markup'. Otherwise, Clausewitz won't know what to do with it.

Make sure that your localisation file has 'l_klingon: ' written on the very first line and nothing else (substituting 'klingon' for your native language, unless you're actually a Klingon). And, every single line after that MUST have a single space at the start, or else it won't work. Your loc files should ALWAYS end with the language they're written for, and should be in their proper folder.

    /mod/MyPersonalityMod/localisation/klingon/mypersonality_l_klingon.yml

If you're replacing text that's anywhere in any other file in the vanilla game, then you need to put it in a folder named 'replace'. If you don't do this, you will make the game crash before it loads. I'm telling you now to save you a lot of pain later on, so ignore my warning at your risk.

    /mod/MyPersonalityMod/localisation/klingon/replace/mypersonality_overwrites_l_klingon.yml


For your own sanity, here's a template for you:

l_klingon:
 #Greetings
 XX_FRIENDLY_GREETING_01:0 ""
 XX_NEUTRAL_GREETING_01:0 ""
 XX_HOSTILE_GREETING_01:0 ""

Everything should, more or less, look like that. Yes, the zeroes are necessary for English. No, I don't know why, I taught myself how to do this through trial and error, so no one's explained it to me. As long as all your loc files have their proper language name in the first line and at the end of the filename, you can name them whatever you like. I use this to organize them so I know what's in each file.


## Why did you make such a stupid mod? That's a lot of effort for one dumb joke.

You're damn right it is, and I still think it's hilarious.

When I first downloaded Ethics and Civics Classic, I decided that it would be really funny to make a Fanatic Pacifist-Ecocentrist empire. When I found Cybrxkhan's monstrously huge namelist and saw the Space Hippies on it, I quickly found my favorite roleplay empire. I found myself cracking dumb jokes with no audience, and decided that it was amusing enough that someone else would have found it funny. So, I just... kinda did it.

I was originally going to go through all of the 1987 Teenage Mutant Ninja Turtles TV series and get snippets of Townsend Coleman's performance as Michelangelo for the advisor voice. But as I started, I realized that most of the voicelines I would be able to extract would have had blasters, swords, and 80s triangle synth in the background. And even then, they likely wouldn't be relevant to what was happening in the game. That, and the last thing I wanted was to get a DMCA notice from a childhood hero.

As much as I'd love to pay one of my extremely talented voice-acting friends to do this for me, I can't afford their rates. They are professionals, after all, and voice acting is VERY hard work. It's worth paying people for, and I have no money. So, I dusted off my shitty old Blue Yeti and decided to take a whack at it myself.

That's pretty much it.
