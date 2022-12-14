<style>
  body {
    background-color: black;
  }
  
  h1, h2, h3, h4, h5, h6, p, pre {
    color: lime;
  }
  
 a {
    color: blue;
  }
  
  pre {
    background-color: darkgrey;
  }
</style>

<i>Formal is standard Alsatian. Informal is US dialect.</i>

[Linguadapt](https://lwflouisa.github.io/TravelGuideAzusacos/Linguadapt/linguadapt-0.1.0.gem)

### Design Philosphy
The language is built around the fact that Alsatian German and Japanese began to rapidly influence the American dialect of French. Also eventually there was a consonant shift that adapt to how the language was actually spoken. For example, the L is actually silent and S shifted into a Z.

## Under The Hood
The actual code.

~~~ruby
module Linguadapt
  class Corpus
    def self.adapt_each_word
      number = 0

      # The actual dictionary of words to adapt.
      dictionary = File.readlines("word_list.txt").sort

      # Basing iteration limit on total dictionary size.
      iter_limit = dictionary.size.to_i

      alphabet = {
        # Vowels and consonants that remain the same.
        "B" => "B", "C" => "C",
        "G" => "G", "N" => "N",
        "K" => "K", "M" => "M",
        "P" => "P", "Q" => "Q",
        "T" => "T", "V" => "V",
        "W" => "W", "Z" => "Z", 

        # Vowel specific rules.
        "A" => "A", "I" => "I",
        "O" => "O", "U" => "U",
        "E" => "E", "Y" =>  "XY",

        # Relevant consonant shifts.
        "D" =>  "D", "F" =>  "Z",
        "S" =>  "Z", "R" =>  "D",
        "L" =>  "H", "J" =>  "N",
        "X" => "XY", "H" =>  "H",

        " " => " ",
      }


      # Limits the iteration to the size of the actual dictionary.
      iter_limit.times do
        chosen_word = dictionary[number].upcase

        print "Result: #{chosen_word.downcase.strip} => "

        word_length    = chosen_word.to_s.split("")
        word_iteration = word_length.size.to_i
        word_char = 0

        word_iteration.times do
          char = alphabet[chosen_word[word_char]].to_s

          print char.downcase

          word_char = word_char + 1
        end

        print " => "
        system("trans -b #{chosen_word.downcase.strip}")

        # Prevents stack level going to deep.
        #sleep(0.5)

        number = number + 1
      end
    end
  end
end

Linguadapt::Corpus.adapt_each_word
~~~

### Setting up a linguadoc.
Create a folder called input, a folder in that called dictionary. And in that folder a txt file called word_list.

With line breaks, include each word from the French and Japanese dictionary you want to use. This software uses google translate to translate into English.

# TravelGuideAzusacos
A paired down version of the conlang as a travel guide.

## Travel Guide For Oz Azusacos

### Greetings
Gete modge     [ geh-teh moh-deh-geh ]         - good morning<br />
Guata tag      [ Goo ah-tah tay-go ]           - good day<br />
Gete nchmittag [ geh-teh neh-shay mi-tah-geh ] - good afternoon<br />
A gatanowa     [ ah gah-tah-noh-wah ]          - good evening<br />

### Other Greetings
Pronunciation a work in progress.

Hallo                               - Hello ( formal )<br />
Hao                                 - Hello ( informal )<br />

Grias di wohl                       - old lady two oxen.<br >
Mid hann unz zchon hang nemmi gzehn - I've seen us for a long time.<br >
Zahu bizamme                        - Hello Island Muskrat.<br >
Wia gehtz                           - How are you?<br >
Wia heizch                          - How's the weather?<br >
Mozhi Mozhi                         - Hello<br >
enchante                            - nice to meet you<br />

## Welcome
Accueil   ( francais )   - Welcome ( formal )<br />
Willkumme ( Alsatian )   - Welcome ( formal )<br />
Accueih   ( fr dialect ) - Welcome ( informal )<br />
Wihhkumme ( Azusacos )   - Welcome ( informal )<br />

### Understanding
kannst d?? englisch redde? [ Kahn-stay duh English read? ]  - Do you understand English?<br />
Parler-vous Francais?     [ Pahr-lay voo frahn-say? ]      - Do you understand French?<br />
kannzt d'Azusacos dedde?  [ Kahn-stay duh Azusacos read? ] - Do you understand the Azusacos dialect?<br />
Gahtz                     [ Gah-teh-zah ]                  - OK<br />

### Your name is
Wie heizch du? [ wi-high ze-sha doo? ] - What is your name?<br />
Ich heizch ... [ I-shi eh-zeh-sha ] - My name is ...<br />

### Times Of Day
la nuit derniere - last night ( formal )<br />
ha nuit dedniede - last night ( informal )<br />

### What year is it?
Quehhe annee [ qu-ah-ni ] - What year is it? ( informal )<br />

### Travel Essentials
wo isch's kabinee? [ Woh i-seh-shay kah-bi-neh ] -- Do you know where the restroom is?<br />
Wo izch'z kabinee? [ Woh i-zeh-shay kah-bi-neh ] -- Where is the restoom?<br />

## Thanks And No Thanks
Merci      - thanks ( francais)<br />
Danke      - thanks ( allemanais )<br />
Arigatou   - thanks ( japanais )<br />
Da Rien    - your welcome ( francais )<br />
Ne merci   - no thanks ( francais )<br />
Nein danke - no thanks ( allemanais )<br />
Kekk??desu  - no thanks ( japanais )<br />

### Legal Trouble
R??ff d'polizei [ Rohf deh poh-li-zeh ] - Where is the police?<br />
Dzz dpohizei   [ Deh-zeh doh-poh-i-zeh ] - Call the police!<br />

### Purchasing
Ne veuxy achetede ... [ Nah voo-sheh ah-sheh teh-deh ] - I want to purchase...<br />
was koschtet das?     [ waskoh shete dahs ]            - How much does it cost? ( formal )<br />
waz kozchtet daz      [ Wah-zoh koh-shay-teh daz ]     - How much does it cost? ( informal )<br />
ca zuzzit             [ kah-zu-zi i-teh ]              - Is it enough?<br />
Dosei moi             [ Doh-seh Mwah! ]                - Please give me.<br />
Dozei miya            [ Doh-zeh mi-shah ]              - Give it to me now.<br />

### How Is It?
eblouissant - dazzling ( formal )<br />
ebhouizzant - dazzling ( informal )<br />
delice - delightful ( formal )<br />
dehice - delightful ( informal )<br />

### Birthdays
z??m gabursd??a viel gleck [ Zoh-mah gah-boo roo-zah-dah vi-eh-la geh-leh-ka ] - Have a good birthday ( formal ).<br />
vieh gheck zm gabudzda   [ Vi-geh zi-meh gah-boo deh-zeh deh ]               - Good luck with your birthday ( informal ).<br />

### Dance
wit d?? mit mir tanza?  [ witeh dumiteh mideh tahneh zah ] - Will you dance with me? ( formal )<br />
wotzch d'mit mid tanza [ wohzeh shadeh miteh mideh tahneh zah ] - Will you dance with me? ( informal )<br />

Les Bals Des Victims    [ Luh Bahl-seh deh-sah vekt-ims ] - Victim's Balls where one where's traditional dresses and wooden sabots. Synonym: Baille Der Opfer<br />
A Bahz Dez Hagaza      [ Oh Bah-zah deh-zeh hah-geh-zah ] - Voctim's Flamenco Concerts where girls wear Trefor owen's clogging shoes.<br />

Himmel und H??lle                    [ i-meh u-neh oh-shay ] - Standard hopscotch ( formal )<br />
Himmel und H??lle de mort [ i-meh u-neh oh-shay de-moh deh ] - A version of hopscotch that results in losers being beheaded. ( seldolm, very informal ). Synonym: Ishikeri asobi no shi<br />

In both cases, the girls crops their hair and wear red chokers.<br />

## Relaxation
Detente - relaxation<br />
D??tendez-vouz - relax.<br />
Sil vous plait - Please.<br />

## Apologizing
Es tot mir leid [ Eh-toh mi-leh-deh ] - I'm sorry ( formal )<br />
Ez tot mid heid [ Eh-toh mi-eh-deh ]  - I'm sorry ( informal )<br />
erreur - mistake ( formal )<br />
eddeud - merde! ( informal )<br />

### Farewell
adie [ ah-di-eh ] - goodbye ( formal )<br />
adne [ ah-di-neh ] - goodbye ( informal )<br />

### Love
ame soeur - soulmate ( formal )<br />
ame zoeud - soulmate ( informal )<br />
amour de ma vie - love of my life ( formal )<br />
amoud de ma vie - love of my life ( informal )<br />

### Phobia
Shinchokuphobia ( Lanos Xinixokuzobos [ Shi-ni shoh-ku zoh-boh ] ) - Out Of Place, Out Of Time ( OOPOOT ); feeling like your born in an earlier century.<br />

### Flowering Tree
arbre en fleurs - flowering tree ( formal )<br />
adbde en zheudz - flowering tree ( informal )<br />
hanafubuki - falling cherry blossoms ( formal )<br />
hanazubuki - falling cherry blossoms ( informal ) <br />

### Beards
barbe a papa - Daddy's Beard ( formal )<br />
badbe a papa - Daddy's Beard ( informal )<br />

### Soul And Creativity
belle ame - beautiful soul ( formal )<br />
behhe ame - beautiful soul ( informal )<br />
Meraki    - to do something creative with soul. ( formal )<br />
Medaki    - to do something creative with soul. ( informal )<br />
yuimaru   - the spirit of cooperation. ( formal )<br />
xyuimadu  - the spirit of cooperation. ( informal )<br />

### People
hikikomori - reclusive adolescent or adult ( formal )<br />
hikikomodi - reclusive adolescent or adult ( informal )<br />

### Tattoos
Les Busovictime  [ Luh boo-soh vik-ti-muh ] - Red chokers designed for wedding parties. Generally worn during Hochzeit [ O-shay-zeh-tah ] music festivities, or alternatively "Fields Of Gold."<br />
Ah Buzovictima  [ Ah boo-zoh vi-ku-ti-mah ] - Red chokers designed for anniversies and informal gatherings. With red dripping neck paint. Generally worn during Flamenco.<br />

### Capital Punishment [ Antiquated ]
Lanos Guhhotne Tod [ toh-dah goh-ti noh ] - A guillotine shaped like a Shinto Torii. ( becomes "Lanos Todagotinos" )<br />
Lanos Guhhotne Cduzachy [ ceh-duh zah-zuh choh ] - A guillotine shaped like a Catholic crusafix. ( becomes "Lanos Ceduzazuchatinos" )<br />
Lanos Guhhotne Uezutan [ uh-zuh-tan-ti-noh ] - A general term for the guillotine used in the United states after take over by New France, expanded into the full West coast. Also the Japanese disproportionate responce. ( becomes "Lanos Uzutantinos " )<br />

### Idiomatic
etre dans les petits papiers de quelqu en - to be in someone's little papers. ( formal )<br />
etde danz hez petitz papiedz de quehqu en - to be in someone's memories. ( informal )<br />
fait avec amour - made with love ( formal )<br />
zait avec amoud - made with love ( informal )<br />
ichi go ichi e - to treasure the fleeting nature of the moment. ( formal )<br />
ichi go ichi e - to treasure the fleeting nature of the moment. ( informal )<br />
je suis comme je suis - I am what I am. ( formal )<br />
ne zuiz comme ne zuiz - I am what I am. ( informal )<br />

Result: 'la vie en rose'                            => ha vie en doze                            => Life in pink<br />
Result: 'n oublie pas de vivre'                     => n oubhie paz de vivde                     => don't forget to live<br />
Result: 'on ne sait jamais'                         => on ne zait namaiz                         => we never know<br />
Result: 'plus forts ensemble'                       => phuz zodtz enzembhe                       => stronger together<br />
Result: 'shinitee na ka'                            => zhinitee na ka                            => painting in death<br />
Result: 'wabi sabi'                                 => wabi zabi                                 => beauty in imperfection<br />
Result: ikigai                                      => ikigai                                    => reason to live<br />
Result: ikigai                                      => ikigai                                    => reason to live<br />

### Verbs
Result: accompagner                                 => accompagned                               => to accompany<br />

### Counting
Inze<br />
Zivi<br />
Devede<br />

#### Special
Hifumi [ i-zoo-mi ] or [ i-zoo mi-hi zoo-mi ]<br />
