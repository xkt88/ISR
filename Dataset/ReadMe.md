# Benchmarking and Improving Abstract Visual Reasoning via Multimodal Self-Refinement

This repository contains the dataset and prompts for the paper "Benchmarking and Improving Abstract Visual Reasoning via Multimodal Self-Refinement."

## Overview

We introduce a multi-domain benchmark of **1,800 abstract concepts** across six culturally diverse domains, rendered in **Cartoon** and **Minimalist** styles. The benchmark enables systematic evaluation of text-to-image models on figurative content beyond literal alignment.

### Domains

| Domain | Description | Count |
|--------|-------------|-------|
| Public Figures | Notable individuals across entertainment, science, politics, sports | 300 |
| Film & TV | Movies and television series | 300 |
| Literary Works | Books, plays, poems, and folklore | 300 |
| Fictional Characters | Characters from mythology, literature, games, and media | 300 |
| Idioms | English idiomatic expressions | 300 |
| Places | Cities and landmarks worldwide | 300 |

---

## Dataset

All concept lists are provided below in a single code block for convenient copying:

```python
# Public Figures (300 items)
names = ["Abraham Lincoln", "Adele", "Agatha Christie", "Al Pacino", "Albert Einstein", "Alfred Hitchcock", "Amy Winehouse", "Andy Serkis", "Angela Merkel", "Angelina Jolie", "Anne Hathaway", "Anthony Hopkins", "Anton Chekhov", "Anya Taylor-Joy", "Ariana Grande", "Arnold Schwarzenegger", "Audrey Hepburn", "Barack Obama", "Barbra Streisand", "Beethoven", "Ben Affleck", "Ben Kingsley", "Benedict Cumberbatch", "Benjamin Franklin", "Bette Davis", "Beyonce", "Bill Gates", "Bill Murray", "Billie Eilish", "Bob Dylan", "Bob Marley", "Boris Johnson", "Brad Pitt", "Brigitte Bardot", "Bruce Lee", "Bruce Willis", "Bruno Mars", "Cate Blanchett", "Celine Dion", "Charles Darwin", "Charlie Chaplin", "Charlize Theron", "Christian Bale", "Christine Lagarde", "Christopher Walken", "Cillian Murphy", "Clark Gable", "Clint Eastwood", "Conan O'Brien", "Condoleezza Rice", "Cristiano Ronaldo", "Daniel Craig", "Daniel Radcliffe", "Danny Devito", "David Bowie", "Demi Moore", "Denzel Washington", "Diego Maradona", "Donald Sutherland", "Donald Trump", "Drake", "Dustin Hoffman", "Dwayne Johnson", "Ed Sheeran", "Edward Norton", "Elijah Wood", "Elizabeth Taylor", "Elle Fanning", "Ellen Degeneres", "Elon Musk", "Elton John", "Elvis Presley", "Eminem", "Emma Stone", "Emma Watson", "Ernest Hemingway", "Erwin Schrödinger", "Eva Green", "Forest Whitaker", "Frank Sinatra", "Franz Kafka", "Freddie Mercury", "Frida Kahlo", "Gabriel Garcia Marquez", "Gareth Bale", "Gary Oldman", "Geoffrey Rush", "George Clooney", "George Lucas", "George Washington", "Gordon Ramsay", "Gregory Peck", "Greta Thunberg", "Halle Berry", "Harrison Ford", "Hedy Lamarr", "Helen Hunt", "Helena Bonham Carter", "Henry Cavill", "Hillary Clinton", "Hugh Jackman", "Hugh Laurie", "Humphrey Bogart", "Ian Mckellen", "Ingrid Bergman", "Isaac newton", "Jane Goodall", "J.K. Rowling", "J.K. Simmons", "Jack Black", "Jack Nicholson", "Jackie Chan", "Jake Gyllenhaal", "James Cagney", "Javier Bardem", "Jean Reno", "Jeff Bezos", "Jeff Goldblum", "Jennifer Aniston", "Jennifer Connelly", "Jennifer Lopez", "Jerry Seinfeld", "Jim Carrey", "Jim Morrison", "Joaquin Phoenix", "Jodie Foster", "Joe Biden", "John C. Reilly", "John Krasinski", "John Lennon", "John Malkovich", "John Travolta", "John Wayne", "Johnny Depp", "Judi Dench", "Julia Roberts", "Julianne Moore", "Justin Bieber", "Kamala Harris", "Kanye West", "Karl Lagerfeld", "Kate Beckinsale", "Katharine Hepburn", "Katy Perry", "Keanu Reeves", "Keira Knightley", "Kevin Spacey", "Kim Kardashian", "Kobe Bryant", "Kristen Stewart", "Kristin Scott Thomas", "Lady Gaga", "Larry King", "Laurence Fishburne", "Leonardo DiCaprio", "Leslie Nielsen", "Lewis Hamilton", "Liam Neeson", "Lil Nas X", "Lionel Messi", "Liv Tyler", "Liza Minnelli", "Luciano Pavarotti", "Luka Modric", "Macaulay Culkin", "Madonna", "Mads Mikkelsen", "Maggie Smith", "Mahatma Gandhi", "Manny Pacquiao", "Margaret Thatcher", "Margot Robbie", "Maria Callas", "Mariah Carey", "Marilyn Monroe", "Marion Cotillard", "Mark Twain", "Mark Wahlberg", "Mark Zuckerberg", "Marlene Dietrich", "Martin Luther King", "Martin Scorsese", "Matt Damon", "Matthew Mcconaughey", "Meg Ryan", "Megan Fox", "Mel Gibson", "Meryl Streep", "Michael Caine", "Michael Douglas", "Michael Jackson", "Michael Jordan", "Michael Phelps", "Michelle Pfeiffer", "Mick Jagger", "Mike Tyson", "Mila Kunis", "Miley Cyrus", "Monica Bellucci", "Morgan Freeman", "Mother Teresa", "Muhammad Ali", "Napoleon Bonaparte", "Natalie Portman", "Neil deGrasse Tyson", "Nelson Mandela", "Nicki Minaj", "Nicolas Cage", "Nicole Kidman", "Nikola Tesla", "Novak Djokovic", "Octavia Spencer", "Omar Sharif", "Oprah Winfrey", "Owen Wilson", "Pablo Picasso", "Paris Hilton", "Patrick Dempsey", "Paul Mccartney", "Paul Walker", "Pedro Pascal", "Pep Guardiola", "Peter Dinklage", "Philip Seymour Hoffman", "Prince Harry", "Princess Diana", "Queen Elizabeth", "Quentin Tarantino", "Rachel Weisz", "Rafael Nadal", "Ralph Fiennes", "Rami Malek", "Ray Charles", "Reese Witherspoon", "Richard Gere", "Rihanna", "Robbie Williams", "Robert De Niro", "Robert Downey Jr", "Robert Pattinson", "Roberto Benigni", "Robin Williams", "Roger Federer", "Ronald Reagan", "Russell Crowe", "Ryan Gosling", "Ryan Reynolds", "Sally Field", "Sam Smith", "Samuel L. Jackson", "Sandra Bullock", "Scarlett Johansson", "Sean Connery", "Sean Penn", "Shakira", "Shaquille O'Neal", "Sharon Stone", "Shawn Mendes", "Sigmund Freud", "Sigourney Weaver", "Simon Cowell", "Simone De Beauvoir", "Snoop Dogg", "Stan Lee", "Stephen Curry", "Stephen King", "Steve Carell", "Steve Harvey", "Steve Jobs", "Steve Martin", "Steve McQueen", "Steven Spielberg", "Sting", "Susan Boyle", "Susan Sarandon", "Sylvester Stallone", "Taylor Swift", "The Weeknd", "Tiger Woods", "Tilda Swinton", "Tim Robbins", "Timothee Chalamet", "Tobey Maguire", "Thomas Edison", "Tom Cruise", "Tom Hanks", "Tom Hardy", "Tom Holland", "Tom Selleck", "Tommy Lee Jones", "Uma Thurman", "Vin Diesel", "Vincent Van Gogh", "Whoopi Goldberg", "Will Ferrell", "Will Smith", "William Shakespeare", "Woody Allen", "Zendaya", "Zinedine Zidane"]

# Film & TV (300 items)
mvtv = ["101 Dalmatians (Movie)", "12 Angry Men (Movie)", "127 Hours (Movie)", "3 Idiots (Movie)", "500 Days of Summer (Movie)", "A Star Is Born (Movie)", "Ace Ventura Pet Detective (Movie)", "Aladdin (Movie)", "Alice in Wonderland (Movie)", "Alien (Movie)", "American History X (Movie)", "American Pie (Movie)", "Amélie (Movie)", "Apollo 13 (Movie)", "Aquaman (Movie)", "Arcane (TV)", "Arrival (Movie)", "Avatar (Movie)", "Back to the Future (Movie)", "Band of Brothers (TV)", "Barbie (Movie)", "A Beautiful Mind (Movie)", "Beetlejuice (Movie)", "Better Call Saul (TV)", "The Big Bang Theory (TV)", "Big Hero 6 (Movie)", "Bird Box (Movie)", "Black Mirror (TV)", "Black Panther (Movie)", "Black Swan (Movie)", "Blade Runner (Movie)", "Blood Diamond (Movie)", "Bohemian Rhapsody (Movie)", "The Boys (TV)", "Braveheart (Movie)", "Breakfast at Tiffany's (Movie)", "Breaking Bad (TV)", "Bridgerton (TV)", "Brokeback Mountain (Movie)", "Brooklyn Nine-Nine (TV)", "Cars (Movie)", "Casablanca (Movie)", "Casino Royale (Movie)", "Cast Away (Movie)", "Catch Me If You Can (Movie)", "Charlie and the Chocolate Factory (Movie)", "Chernobyl (TV)", "Chinatown (Movie)", "A Christmas Carol (Movie)", "Cinderella (Movie)", "Citizen Kane (Movie)", "A Clockwork Orange (Movie)", "Coco (Movie)", "Community (TV)", "Coraline (Movie)", "Corpse Bride (Movie)", "Cowboy Bebop (TV)", "Curb Your Enthusiasm (TV)", "Chernobyl (Movie)", "Deadpool (Movie)", "Dead Poets Society (Movie)", "The Departed (Movie)", "Despicable Me (Movie)", "Dexter (TV)", "Die Hard (Movie)", "Django Unchained (Movie)", "Doctor Strange (Movie)", "Doctor Who (TV)", "Donnie Darko (Movie)", "Downton Abbey (TV)", "Drive (Movie)", "Dumb and Dumber (Movie)", "Dune (Movie)", "Edward Scissorhands (Movie)", "Elemental (Movie)", "Encanto (Movie)", "Enter the Dragon (Movie)", "E.T. the Extra-Terrestrial (Movie)", "Euphoria (TV)", "Everything Everywhere All At Once (Movie)", "Ex Machina (Movie)", "The Exorcist (Movie)", "Family Guy (TV)", "Fargo (Movie)", "Ferris Bueller's Day Off (Movie)", "Fight Club (Movie)", "Finding Nemo (Movie)", "Fleabag (TV)", "Forrest Gump (Movie)", "Friends (TV)", "Frozen (Movie)", "Full Metal Jacket (Movie)", "Futurama (TV)", "Game of Thrones (TV)", "Gangs of New York (Movie)", "Get Out (Movie)", "Ghostbusters (Movie)", "Gladiator (Movie)", "Gone Girl (Movie)", "Good Will Hunting (Movie)", "GoodFellas (Movie)", "The Godfather (Movie)", "The Goonies (Movie)", "Gravity (Movie)", "Grease (Movie)", "The Green Mile (Movie)", "Grey's Anatomy (TV)", "Groundhog Day (Movie)", "Guardians of the Galaxy (Movie)", "The Handmaid's Tale (TV)", "The Hangover (Movie)", "Harry Potter (Movie)", "Heat (Movie)", "Her (Movie)", "Hercules (Movie)", "High School Musical (Movie)", "Home Alone (Movie)", "House M.D. (TV)", "House of Cards (TV)", "How I Met Your Mother (TV)", "How to Train Your Dragon (Movie)", "The Hunger Games (Movie)", "I Am Legend (Movie)", "Ice Age (Movie)", "Inception (Movie)", "The Incredibles (Movie)", "Indiana Jones (Movie)", "Inglourious Basterds (Movie)", "Inside Out (Movie)", "Interstellar (Movie)", "Iron Man (Movie)", "It (Movie)", "It's a Wonderful Life (Movie)", "It's Always Sunny in Philadelphia (TV)", "James Bond (Movie)", "Jaws (Movie)", "John Wick (Movie)", "Joker (Movie)", "The Jungle Book (Movie)", "Jurassic Park (Movie)", "Kill Bill (Movie)", "King Kong (Movie)", "Knives Out (Movie)", "Kung Fu Panda (Movie)", "Lady and the Tramp (Movie)", "La La Land (Movie)", "The Last of Us (TV)", "Lawrence of Arabia (Movie)", "Léon The Professional (Movie)", "Life Is Beautiful (Movie)", "Life of Pi (Movie)", "The Lion King (Movie)", "Little Miss Sunshine (Movie)", "The Little Mermaid (Movie)", "Lost (TV)", "Lost in Translation (Movie)", "The Mandalorian (TV)", "The Mask (Movie)", "Mad Max(Movie)", "Madagascar (Movie)", "Mean Girls (Movie)", "Memento (Movie)", "Men in Black (Movie)", "Minions (Movie)", "Mission Impossible (Movie)", "Moana (Movie)", "Modern Family (TV)", "Money Heist (TV)", "Monsters, Inc. (Movie)", "Monty Python and the Holy Grail (Movie)", "Moonlight (Movie)", "Mrs. Doubtfire (Movie)", "Mulan (Movie)", "The Mummy (Movie)", "My Fair Lady (Movie)", "Narcos (TV)", "National Treasure (Movie)", "The Nightmare Before Christmas (Movie)", "No Country for Old Men (Movie)", "The Notebook (Movie)", "Ocean's Eleven (Movie)", "The Office (TV)", "One Flew Over the Cuckoo's Nest (Movie)", "Oppenheimer (Movie)", "Paddington Bear (Movie)", "Parasite (Movie)", "Parks and Recreation (TV)", "Peaky Blinders (TV)", "Peter Pan (Movie)", "Pinocchio (Movie)", "Pirates of the Caribbean (Movie)", "Planet of the Apes (Movie)", "The Prestige (Movie)", "Pretty Woman (Movie)", "Pride and Prejudice (Movie)", "Prison Break (TV)", "Psycho (Movie)", "Pulp Fiction (Movie)", "A Quiet Place (Movie)", "Rambo (Movie)", "Ratatouille (Movie)", "Rear Window (Movie)", "Reservoir Dogs (Movie)", "Rick and Morty (TV)", "Robin Hood (Movie)", "Rocky (Movie)", "Roman Holiday (Movie)", "Saving Private Ryan (Movie)", "Scarface (Movie)", "Schindler's List (Movie)", "School of Rock (Movie)", "Scream (Movie)", "Se7en (Movie)", "Seinfeld (TV)", "Shameless (TV)", "The Shawshank Redemption (Movie)", "Sherlock (TV)", "The Shining (Movie)", "Shrek (Movie)", "Shutter Island (Movie)", "The Silence of the Lambs (Movie)", "The Simpsons (TV)", "Singin' in the Rain (Movie)", "The Sixth Sense (Movie)", "Sleeping Beauty (Movie)", "Slumdog Millionaire (Movie)", "Snatch (Movie)", "Snow White (Movie)", "The Social Network (Movie)", "Sonic the Hedgehog (Movie)", "The Sopranos (TV)", "The Sound of Music (Movie)", "South Park (TV)", "Space Jam (Movie)", "Spider-Man (Movie)", "Spirited Away (Movie)", "Squid Game (TV)", "Stand by Me (Movie)", "Star Trek (Movie)", "Star Wars (Movie)", "Stranger Things (TV)", "Succession (TV)", "Suits (TV)", "Super Mario Bros. (Movie)", "Superbad (Movie)", "Superman (Movie)", "Tangled (Movie)", "Tarzan (Movie)", "Ted (Movie)", "Ted Lasso (TV)", "The Terminator (Movie)", "Taxi Driver (Movie)", "The Addams Family (Movie)", "The Avengers (Movie)", "The Bourne Identity (Movie)", "The Crown (TV)", "The Devil Wears Prada (Movie)", "The Fifth Element (Movie)", "The Graduate (Movie)", "The Great Gatsby (Movie)", "The Grinch (Movie)", "The Karate Kid (Movie)", "The Last King of Scotland (Movie)", "The Lord of the Rings (Movie)", "The Legend of 1900 (Movie)", "The Martian (Movie)", "The Matrix (Movie)", "The Pianist (Movie)", "The Polar Express (Movie)", "The Queen's Gambit (TV)", "The Walking Dead (TV)", "The Wire (TV)", "The Wolf of Wall Street (Movie)", "Thor (Movie)", "Titanic (Movie)", "Top Gun (Movie)", "Toy Story (Movie)", "Trainspotting (Movie)", "Transformers (Movie)", "Tron (Movie)", "Troy (Movie)", "True Detective (TV)", "The Truman Show (Movie)", "Twilight (Movie)", "Twin Peaks (TV)", "Two and a Half Men (TV)", "Up (Movie)", "Us (Movie)", "V for Vendetta (Movie)", "Wall-E (Movie)", "Wednesday (TV)", "Westworld (TV)", "Whiplash (Movie)", "The Wizard of Oz (Movie)", "Wolverine (Movie)", "Wonder Woman (Movie)", "The X-Files (TV)", "X-Men (Movie)", "Yellowstone (TV)", "Zootopia (Movie)"]

# Literary Works (300 items)
literary_works = ["12 Years a Slave", "20,000 Leagues Under the Sea", "A Christmas Carol", "A Clockwork Orange", "A Dream of Red Mansions", "A Game of Thrones", "A Little Princess", "A Midsummer Night's Dream", "A Tale of Two Cities", "A Wrinkle in Time", "Aesop's Fables", "Adventures of Huckleberry Finn", "Aladdin", "Ali Baba and the Forty Thieves", "Alice in Wonderland", "All Quiet on the Western Front", "American Gods", "American Psycho", "Angels & Demons", "Animal Farm", "Anna Karenina", "Anne of Green Gables", "Around the World in 80 Days", "Artemis Fowl", "Atlas Shrugged", "Beauty and the Beast", "Beloved", "Beowulf", "Black Beauty", "Bleak House", "Bluebeard", "Brave New World", "Bridge to Terabithia", "Brother and Sister", "Carrie", "Catch-22", "Charlie and the Chocolate Factory", "Charlotte's Web", "Cinderella", "Cloud Atlas", "Cloudy with a Chance of Meatballs", "Corduroy", "Coraline", "Crazy Rich Asians", "Crime and Punishment", "David Copperfield", "Death of a Salesman", "Divergent", "Do Androids Dream of Electric Sheep?", "Doctor Zhivago", "Don Quixote", "Dracula", "Dune", "Emma", "Ender's Game", "Eragon", "Fahrenheit 451", "Faust", "Fear and Loathing in Las Vegas", "Fight Club", "Flowers for Algernon", "For Whom the Bell Tolls", "Frankenstein", "Goblin Market", "Goldilocks and the Three Bears", "Gone with the Wind", "Good Omens", "Goodnight Moon", "Goosebumps", "Great Expectations", "Green Eggs and Ham", "Gulliver's Travels", "Hamlet", "Hans My Hedgehog", "Hansel and Gretel", "Harold and the Purple Crayon", "Harry Potter", "Hatchet", "Heart of Darkness", "Heidi", "His Dark Materials", "Holes", "Horton Hears a Who!", "How the Grinch Stole Christmas!", "Howl", "I, Robot", "Interview With the Vampire", "If You Give a Mouse a Cookie", "Inferno", "Into the Wild", "Invisible Man", "It", "Jack and the Beanstalk", "Jack the Giant Killer", "James and the Giant Peach", "Jane Eyre", "Jaws", "Jonathan Livingston Seagull", "Journey to the West", "Jumanji", "Jurassic Park", "King Arthur and His Knights of the Round Table", "King Lear", "Les Misérables", "Life of Pi", "Little Miss Muffet", "Little Red Riding Hood", "Little Women", "Llama Llama Red Pajama", "Long Walk to Freedom", "Lord Jim", "Lord of the Flies", "Macbeth", "Madeline", "Mary Poppins", "Memoirs of a Geisha", "Midnight's Children", "Milk and Honey", "Misery", "Miss Peregrine's Home for Peculiar Children", "Mistborn", "Moby-Dick", "Mother Hulda", "Much Ado About Nothing", "Murder on the Orient Express", "Nancy Drew", "Neuromancer", "No Country for Old Men", "Of Mice and Men", "Oh, the Places You'll Go!", "Oliver Twist", "One Flew Over the Cuckoo's Nest", "One Hundred Years of Solitude", "Othello", "Outlander", "Paddington Bear", "Papillon", "Percy Jackson & The Olympians", "Persepolis", "Peter Pan", "Pet Sematary", "Pinocchio", "Pippi Longstocking", "Pride and Prejudice", "Puss in Boots", "Rapunzel", "Ready Player One", "Rebecca", "Reynard the Fox", "Rich Dad Poor Dad", "Robinson Crusoe", "Romance of the Three Kingdoms", "Romeo and Juliet", "Rumpelstiltskin", "Sherlock Holmes", "Shogun", "Siddhartha", "Slaughterhouse-Five", "Sleeping Beauty", "Snow Crash", "Snow White", "Snow White and Rose Red", "Steppenwolf", "Stuart Little", "Sunset Beach", "The Adventures of Tom Sawyer", "The Alchemist", "The BFG", "The Book Thief", "The Boy Who Was Never Afraid", "The Bremen Town Musicians", "The Call of the Wild", "The Canterbury Tales", "The Cat in the Hat", "The Catcher in the Rye", "The Chronicles of Narnia", "The Count of Monte Cristo", "The Crucible", "The Da Vinci Code", "The Day the Crayons Quit", "The Diary of a Young Girl", "The Divine Comedy", "The Erlking", "The Exorcist", "The Fisherman and His Wife", "The Fisherman and the Genie", "The Four Agreements", "The Fox and the Crow", "The Frog Prince", "The Girl on the Train", "The Girl with the Dragon Tattoo", "The Giving Tree", "The Godfather", "The Golden Bird", "The Golden Goose", "The Goose Girl", "The Grapes of Wrath", "The Great Gatsby", "The Handmaid's Tale", "The Hitchhiker's Guide to the Galaxy", "The Hobbit", "The Hound of the Baskervilles", "The Hunchback of Notre-Dame", "The Hunger Games", "The Iliad", "The Importance of Being Earnest", "The Jungle", "The Jungle Book", "The Kite Runner", "The Lady of Shalott", "The Last Unicorn", "The Legend of Sleepy Hollow", "The Legend of the White Snake", "The Lion, the Witch and the Wardrobe", "The Little Humpbacked Horse", "The Little Match Girl", "The Little Mermaid", "The Little Prince", "The Lorax", "The Lord of the Rings", "The Lovely Bones", "The Maltese Falcon", "The Martian", "The Maze Runner", "The Merchant of Venice", "The Merry Wives of Windsor", "The Metamorphosis", "The Name of the Rose", "The Name of the Wind", "The Neverending Story", "The Night Circus", "The Nightingale", "The Odyssey", "The Old Man and the Sea", "The Outsiders", "The Phantom of the Opera", "The Picture of Dorian Gray", "The Pied Piper of Hamelin", "The Pisces", "The Polar Express", "The Princess and the Pea", "The Princess Bride", "The Red Shoes", "The Road", "The Scarlet Letter", "The Secret Garden", "The Secret Life of Bees", "The Seven Ravens", "The Shining", "The Silence of the Lambs", "The Stag at the Pool", "The Stand", "The Strange Case of Dr. Jekyll and Mr. Hyde", "The Tale of Genji", "The Tale of Peter Rabbit", "The Three Little Pigs", "The Three Musketeers", "The Time Machine", "The Tinderbox", "The Trial", "The Turn of the Screw", "The Ugly Duckling", "The Underground Railroad", "The Valiant Little Tailor", "The Very Hungry Caterpillar", "The War of the Worlds", "The Waves", "The Wheel of Time", "The Wild Swans", "The Wind in the Willows", "The Wind-Up Bird Chronicle", "The Wishing-Table, the Gold-Ass, and the Cudgel in the Sack", "The Wizard of Oz", "The Wolf and the Seven Young Goats", "Things Fall Apart", "Think and Grow Rich", "Three Men in a Boat", "Thumbelina", "To Kill a Mockingbird", "To the Lighthouse", "Trainspotting", "Treasure Island", "Tuck Everlasting", "Twilight", "Ulysses", "Uncle Tom's Cabin", "Undine", "Vasilisa the Beautiful", "Waiting for Godot", "War and Peace", "Water for Elephants", "Watership Down", "Where the Red Fern Grows", "Where the Sidewalk Ends", "Where the Wild Things Are", "White Fang", "Wicked", "Wonder", "World War Z", "Wuthering Heights"]

# Fictional Characters (300 items)
fictional_characters = ["Achilles (Greek Mythology)", "Agent Smith (The Matrix)", "Albus Dumbledore (Harry Potter)", "Alex DeLarge (A Clockwork Orange)", "Alice (Alice in Wonderland)", "Alien (Alien)", "Amaterasu (Japanese Mythology)", "Amun (Egyptian Mythology)", "Anubis (Egyptian Mythology)", "Anna Karenina(Anna Karenina)", "Aphrodite (Greek Mythology)", "Apollo (Greek Mythology)", "Aquaman (DC Comics)", "Aragorn (The Lord of the Rings)", "Ares (Greek Mythology)", "Artemis (Greek Mythology)", "Arwen (The Lord of the Rings)", "Aslan (The Chronicles of Narnia)", "Athena (Greek Mythology)", "Atlas (Greek Mythology)", "Austin Powers (Austin Powers)", "Baba Yaga (Slavic Folklore)", "Baldur (Norse Mythology)", "Bane (DC Comics)", "Bastet (Egyptian Mythology)", "Batman (DC Comics)", "Bayonetta (Bayonetta)", "Beatrix Kiddo (Kill Bill)", "Beetlejuice (Beetlejuice)", "Beowulf (Beowulf)", "Big Boss (Metal Gear Solid)", "Bilbo Baggins (The Hobbit)", "Black Panther (Marvel Comics)", "Black Widow (Marvel Comics)", "Blade (Marvel Comics)", "Boba Fett (Star Wars)", "Brahma (Hindu Mythology)", "Bumblebee (Transformers)", "C-3PO (Star Wars)", "Captain America (Marvel Comics)", "Captain Hook (Peter Pan)", "Captain Jack Sparrow (Pirates of the Caribbean)", "Catwoman (DC Comics)", "Cerberus (Greek Mythology)", "Cersei Lannister (Game of Thrones)", "Charon (Greek Mythology)", "Chewbacca (Star Wars)", "Chimera (Greek Mythology)", "Chun-Li (Street Fighter)", "Cloud Strife (Final Fantasy)", "Commander Shepard (Mass Effect)", "Conan the Barbarian (Literature)", "Cortana (Halo)", "Count Dracula (Literature)", "Cyclops (Greek Mythology)", "Daedalus (Greek Mythology)", "Daenerys Targaryen (Game of Thrones)", "Daredevil (Marvel Comics)", "Darth Maul (Star Wars)", "Darth Vader (Star Wars)", "Data (Star Trek)", "Davy Jones (Pirates of the Caribbean)", "Deadpool (Marvel Comics)", "Deckard Cain (Diablo)", "Demeter (Greek Mythology)", "Dionysus (Greek Mythology)", "Django Freeman (Django Unchained)", "Dobby (Harry Potter)", "Doctor Doom (Marvel Comics)", "Doctor Manhattan (Watchmen)", "Doctor Strange (Marvel Comics)", "Doctor Who (Doctor Who)", "Don Quixote (Literature)", "Doom Slayer (Doom)", "Dorothy Gale (The Wizard of Oz)", "Draco Malfoy (Harry Potter)", "Durga (Hindu Mythology)", "E.T. (E.T. the Extra-Terrestrial)", "Edward Scissorhands (Edward Scissorhands)", "Eleven (Stranger Things)", "Ellen Ripley (Alien)", "Ellie Williams (The Last of Us)", "Emperor Palpatine (Star Wars)", "Eros (Greek Mythology)", "Ezio Auditore (Assassin's Creed)", "Fenrir (Norse Mythology)", "Forrest Gump (Forrest Gump)", "Frankenstein (Literature)", "Freddy Krueger (A Nightmare on Elm Street)", "Freya (Norse Mythology)", "Frodo Baggins (The Lord of the Rings)", "Galadriel (The Lord of the Rings)", "Gandalf (The Lord of the Rings)", "Ganesha (Hindu Mythology)", "Ganondorf (The Legend of Zelda)", "Garrus Vakarian (Mass Effect)", "General Grievous (Star Wars)", "Geralt of Rivia (The Witcher)", "Ghost Rider (Marvel Comics)", "Ghostface (Scream)", "Gimli (The Lord of the Rings)", "Godzilla (Godzilla)", "Gollum (The Lord of the Rings)", "Gordon Freeman (Half-Life)", "Green Goblin (Marvel Comics)", "Green Lantern (DC Comics)", "Grendel (Beowulf)", "Griffin (Greek Mythology)", "Groot (Guardians of the Galaxy)", "Guan Yu (Chinese Mythology)", "Guanyin (Chinese Mythology)", "Guile (Street Fighter)", "Guinevere (Arthurian Legend)", "Hades (Greek Mythology)", "Han Solo (Star Wars)", "Hannibal Lecter (The Silence of the Lambs)", "Harley Quinn (DC Comics)", "Harry Potter (Harry Potter)", "Hecate (Greek Mythology)", "Heimdall (Norse Mythology)", "Hela (Norse Mythology)", "Helen of Troy (Greek Mythology)", "Hellboy (Hellboy)", "Hephaestus (Greek Mythology)", "Hera (Greek Mythology)", "Hercules (Roman Mythology)", "Hermes (Greek Mythology)", "Hermione Granger (Harry Potter)", "Hestia (Greek Mythology)", "Hitodama (Japanese Folklore)", "Horus (Egyptian Mythology)", "Hulk (Marvel Comics)", "Hydra (Greek Mythology)", "Icarus (Greek Mythology)", "Indiana Jones (Indiana Jones)", "Inigo Montoya (The Princess Bride)", "Iron Man (Marvel Comics)", "Isaac Clarke (Dead Space)", "Isis (Egyptian Mythology)", "Jabba the Hutt (Star Wars)", "Jack Torrance (The Shining)", "Jaime Lannister (Game of Thrones)", "James Bond (James Bond)", "James T. Kirk (Star Trek)", "Jason (Greek Mythology)", "Jason Voorhees (Friday the 13th)", "Jean-Luc Picard (Star Trek)", "Jim Raynor (StarCraft)", "Jin Kazama (Tekken)", "Jinx (League of Legends)", "Joel Miller (The Last of Us)", "John Constantine (Constantine)", "John Marston (Red Dead Redemption)", "John Rambo (Rambo)", "John Wick (John Wick)", "Joker (DC Comics)", "Jon Snow (Game of Thrones)", "Judge Dredd (Judge Dredd)", "Kali (Hindu Mythology)", "Kappa (Japanese Folklore)", "Katniss Everdeen (The Hunger Games)", "King Arthur (Arthurian Legend)", "King Kong (King Kong)", "Kitsune (Japanese Folklore)", "Kratos (God of War)", "Kylo Ren (Star Wars)", "Lady Justice (Symbolism)", "Lakshmi (Hindu Mythology)", "Lancelot (Arthurian Legend)", "Lara Croft (Tomb Raider)", "Leatherface (The Texas Chain Saw Massacre)", "Legolas (The Lord of the Rings)", "Leonidas (300)", "Lex Luthor (DC Comics)", "Liara T'Soni (Mass Effect)", "Link (The Legend of Zelda)", "Liu Kang (Mortal Kombat)", "Loki (Norse Mythology)", "Luke Skywalker (Star Wars)", "Macbeth (Literature)", "Mad Max (Mad Max)", "Mad-Eye Moody (Harry Potter)", "Magneto (Marvel Comics)", "Maleficent (Sleeping Beauty)", "Master Chief (Halo)", "Marty McFly (Back to the Future)", "Mary Poppins (Mary Poppins)", "Maximus Decimus Meridius (Gladiator)", "Medea (Greek Mythology)", "Medusa (Greek Mythology)", "Mega Man (Mega Man)", "Megatron (Transformers)", "Merlin (Arthurian Legend)", "Michael Myers (Halloween)", "Minotaur (Greek Mythology)", "Morpheus (The Matrix)", "Mr. Bean (Mr. Bean)", "Mr. Spock (Star Trek)", "Mulan (Chinese Folklore)", "Mystique (Marvel Comics)", "Nemesis (Greek Mythology)", "Neo (The Matrix)", "Nezha (Chinese Mythology)", "Nick Fury (Marvel Comics)", "Nike (Greek Mythology)", "Obi-Wan Kenobi (Star Wars)", "Odin (Norse Mythology)", "Oedipus (Greek Mythology)", "Oni (Japanese Folklore)", "Optimus Prime (Transformers)", "Orpheus (Greek Mythology)", "Osiris (Egyptian Mythology)", "Pan (Greek Mythology)", "Pandora (Greek Mythology)", "Paul Atreides (Dune)", "Pegasus (Greek Mythology)", "Pennywise (It)", "Perseus (Greek Mythology)", "Perun (Slavic Mythology)", "Peter Pan (Literature)", "Pinhead (Hellraiser)", "Poseidon (Greek Mythology)", "Predator (Predator)", "Princess Leia (Star Wars)", "Princess Zelda (The Legend of Zelda)", "Professor X (Marvel Comics)", "Prometheus (Greek Mythology)", "Pyramid Head (Silent Hill)", "R2-D2 (Star Wars)", "Ra (Egyptian Mythology)", "Raiden (Mortal Kombat)", "Rey (Star Wars)", "Rick Deckard (Blade Runner)", "Robin Hood (English Folklore)", "RoboCop (RoboCop)", "Rocky Balboa (Rocky)", "Rorschach (Watchmen)", "Rubeus Hagrid (Harry Potter)", "Ryu (Street Fighter)", "Samus Aran (Metroid)", "Samwise Gamgee (The Lord of the Rings)", "Santa Muerte (Mexican Folk Religion)", "Sauron (The Lord of the Rings)", "Scarlet Witch (Marvel Comics)", "Scorpion (Mortal Kombat)", "Sekhmet (Egyptian Mythology)", "Sephiroth (Final Fantasy)", "Set (Egyptian Mythology)", "Severus Snape (Harry Potter)", "Sherlock Holmes (Literature)", "Shiva (Hindu Mythology)", "Sif (Norse Mythology)", "Silver Surfer (Marvel Comics)", "Sinbad (Folklore)", "Sisyphus (Greek Mythology)", "Smaug (The Hobbit)", "Sobek (Egyptian Mythology)", "Solid Snake (Metal Gear Solid)", "Sonic the Hedgehog (Sonic the Hedgehog)", "Spider-Man (Marvel Comics)", "Sub-Zero (Mortal Kombat)", "Sun Wukong (Chinese Mythology)", "Supergirl (DC Comics)", "Superman (DC Comics)", "Surya (Hindu Mythology)", "Sweeney Todd (Sweeney Todd)", "T-800 (The Terminator)", "Tarzan (Literature)", "Taurus (Greek Mythology)", "Tengu (Japanese Folklore)", "Thanos (Marvel Comics)", "The Crow (The Crow)", "The Fates (Greek Mythology)", "The Flash (DC Comics)", "The Mandalorian (Star Wars)", "The Phantom (The Phantom of the Opera)", "Theseus (Greek Mythology)", "Thor (Norse Mythology)", "Thoth (Egyptian Mythology)", "Tony Montana (Scarface)", "Travis Bickle (Taxi Driver)", "Trinity (The Matrix)", "Tyler Durden (Fight Club)", "Tyrion Lannister (Game of Thrones)", "V (V for Vendetta)", "Venom (Marvel Comics)", "Venus (Roman Mythology)", "Vito Corleone (The Godfather)", "Voldemort (Harry Potter)", "Walter White (Breaking Bad)", "Wednesday Addams (The Addams Family)", "William Wallace (Braveheart)", "Willy Wonka (Charlie and the Chocolate Factory)", "Wolverine (Marvel Comics)", "Wonder Woman (DC Comics)", "Yoda (Star Wars)", "Yuki-Onna (Japanese Folklore)", "Yurei (Japanese Folklore)", "Zeus (Greek Mythology)", "Zorro (Literature)"]

# Idioms (300 items)
idioms = ["I could eat a horse", "a big fish in a small pond", "a bird in the hand is worth two in the bush", "a brush with death", "a can of worms", "a chip on one's shoulder", "a drop in the bucket", "a feather in one's cap", "a fly on the wall", "a little bird told me", "a piece of the puzzle", "ace up one's sleeve", "add fuel to the fire", "against the clock", "all ears", "all the bells and whistles", "all thumbs", "ants in one's pants", "apple of one's eye", "apple polisher", "armchair critic", "as blind as a bat", "as busy as a bee", "as wise as an owl", "at the end of one's rope", "axe to grind", "back to the drawing board", "backseat driver", "bad apple", "balance the books", "barking up the wrong tree", "basket case", "bats in the belfry", "bear in mind", "beat around the bush", "bed of roses", "behind bars", "bend over backwards", "big cheese", "bird brain", "bite someone's head off", "bite the bullet", "bite the dust", "black sheep of the family", "blanket coverage", "blind date", "blow one's mind", "blow one's own trumpet", "blow one's top", "blue collar", "boiling frog", "born with a silver spoon in one's mouth", "brain versus brawn", "break a leg", "break the ice", "bring home the bacon", "broken heart", "bull in a china shop", "bull's eye", "burn one's bridges", "burn the candle at both ends", "burn the midnight oil", "bury one's head in the sand", "bury the hatchet", "butter someone up", "butterflies in one's stomach", "canary in a coal mine", "carrot and stick", "cash cow", "cast iron stomach", "castle in the air", "cat burglar", "cat got one's tongue", "catch some Zs", "caught red-handed", "chain smoker", "chasing rainbows", "chicken out", "chip off the old block", "clam up", "close shave", "cold feet", "cold shoulder", "cold turkey", "come out of one's shell", "cook the books", "cool as a cucumber", "cost an arm and a leg", "couch potato", "crack the whip", "crocodile tears", "cross one's fingers", "cry over spilled milk", "cry wolf", "cut corners", "dark horse", "dead end", "devil's advocate", "down in the dumps", "drag one's feet", "dressed to kill", "drink like a fish", "drive someone bananas", "drive someone up the wall", "drop the ball", "drunk as a skunk", "eager beaver", "early bird catches the worm", "eat crow", "eat one's words", "egg on one's face", "elbow grease", "elephant in the room", "emotional baggage", "eye candy", "face like thunder", "face the music", "fat cat", "feather one's nest", "feeling blue", "feet of clay", "fifth wheel", "fight fire with fire", "fish out of water", "fishing for compliments", "flash in the pan", "fly off the handle", "foaming at the mouth", "follow in someone's footsteps", "follow the herd", "food for thought", "fork in the road", "frog in one's throat", "from the bottom of one's heart", "get off someone's back", "get one's ducks in a row", "get the ball rolling", "glass half full", "go fly a kite", "golden handshake", "gravy train", "green thumb", "green with envy", "happy as a clam", "hard nut to crack", "have a bone to pick", "have a finger in every pie", "have a heart of gold", "head in the clouds", "head over heels", "heard it through the grapevine", "heart in one's mouth", "hit the books", "hit the ceiling", "hit the hay", "hit the nail on the head", "hit the road", "hit the sack", "hit the spot", "hold one's tongue", "hold your horses", "hot potato", "hung out to dry", "icing on the cake", "in a nutshell", "in a pickle", "in hot water", "in the doghouse", "in the limelight", "in the same boat", "it takes two to tango", "itchy feet", "jump at one's own shadow", "jump for joy", "jump off the page", "jump ship", "jump the shark", "jump through hoops", "keep a lid on it", "keep one's ear to the ground", "keep one's head above water", "kick the bucket", "kick the habit", "kill two birds with one stone", "killing time", "king of the hill", "knock on wood", "leave no stone unturned", "lemon", "lend a hand", "let off steam", "let sleeping dogs lie", "let the cat out of the bag", "lick someone's boots", "light at the end of the tunnel", "like a bat out of hell", "like chalk and cheese", "like a moth to a flame", "like water off a duck's back", "long shot", "lose one's head", "lose one's mind", "make a mountain out of a molehill", "match made in heaven", "miss the boat", "money laundering", "money pit", "monkey business", "monkey on one's back", "my ears are burning", "my hands are tied", "needle in a haystack", "nest egg", "night owl", "not my cup of tea", "on cloud nine", "on pins and needles", "on the ball", "on the fence", "on thin ice", "on top of the world", "once in a blue moon", "one foot in the grave", "out on a limb", "over the moon", "paint oneself into a corner", "pie in the sky", "piece of cake", "play it by ear", "play on words", "play with fire", "poker face", "pot calling the kettle black", "prisoner of one's own mind", "puppy love", "put a cork in it", "put a sock in it", "put one's foot in one's mouth", "put one's money where one's mouth is", "race against time", "raining cats and dogs", "rat race", "red tape", "ring a bell", "rule of thumb", "rule the roost", "saved by the bell", "sitting duck", "skeleton in the closet", "sleep like a log", "smart cookie", "smell a rat", "smoke and mirrors", "snowed under", "speak of the devil", "speak with a forked tongue", "spill the beans", "split hairs", "spoon-feed", "spring chicken", "stab in the back", "steal someone's thunder", "stick one's neck out", "storm in a teacup", "straight from the horse's mouth", "strike while the iron is hot", "swallow a camel", "swan song", "swept off one's feet", "swim with sharks", "take the bull by the horns", "take with a grain of salt", "teacher's pet", "that's the way the cookie crumbles", "the writing on the wall", "thirst for knowledge", "throw in the towel", "throw the baby out with the bathwater", "tighten one's belt", "time flies", "tip of the iceberg", "top banana", "top dog", "tough cookie", "two peas in a pod", "under the microscope", "under the weather", "walk on eggshells", "walk the tightrope", "water under the bridge", "wear one's heart on one's sleeve", "wet behind the ears", "when hell freezes over", "when pigs fly", "window shopping", "wires crossed", "wolf in sheep's clothing", "work like a dog", "yellow-bellied", "zip one's lip"]

# Places (300 items)
places = ["Abu Simbel (landmark)", "Acropolis (landmark)", "Alcázar of Segovia (landmark)", "Amalfi (city)", "Amber Fort (landmark)", "Amsterdam (city)", "Angel Falls (landmark)", "Angkor Wat (landmark)", "Antelope Canyon (landmark)", "Arashiyama Bamboo Grove (landmark)", "Arc de Triomphe (landmark)", "Athens (city)", "Atomium (landmark)", "Avenue of the Baobabs (landmark)", "Bagan (city)", "Banaue Rice Terraces (landmark)", "Bangkok (city)", "Barcelona (city)", "Beijing (city)", "Belem Tower (landmark)", "Bergen (city)", "Berlin (city)", "Berlin TV Tower (landmark)", "Big Ben (landmark)", "Blue Domes Santorini (landmark)", "Blue Lagoon Iceland (landmark)", "Bondi Beach (landmark)", "Borobudur (landmark)", "Boston (city)", "Boudhanath Stupa (landmark)", "Bran Castle (landmark)", "Brandenburg Gate (landmark)", "Brasília (city)", "Brooklyn Bridge (landmark)", "Bruges (city)", "Bryce Canyon (landmark)", "Buckingham Palace (landmark)", "Budapest (city)", "Buenos Aires (city)", "Burj Khalifa (landmark)", "CCTV Headquarters Beijing (landmark)", "CN Tower (landmark)", "Cape Town (city)", "Cappadocia (landmark)", "Carcassonne (city)", "Cartagena (city)", "Casa Batlló (landmark)", "Chapel Bridge Lucerne (landmark)", "Charles Bridge (landmark)", "Chiang Mai (city)", "Chicago (city)", "Chichen Itza (landmark)", "Christ the Redeemer (landmark)", "Chrysler Building (landmark)", "Church of the Savior on Blood (landmark)", "Château de Chambord (landmark)", "Cinque Terre (city)", "Cliffs of Dover (landmark)", "Cologne (city)", "Cologne Cathedral (landmark)", "Colosseum (landmark)", "Copenhagen (city)", "Cusco (city)", "Dancing House Prague (landmark)", "Delphi (landmark)", "Devils Tower (landmark)", "Dolomites (landmark)", "Dresden (city)", "Dublin (city)", "Dubrovnik (city)", "Duomo di Milano (landmark)", "Duomo of Florence (landmark)", "Edinburgh (city)", "Edinburgh Castle (landmark)", "Eiffel Tower (landmark)", "Empire State Building (landmark)", "Ephesus (landmark)", "Fallingwater (landmark)", "Flatiron Building (landmark)", "Florence (city)", "Forbidden City (landmark)", "Fushimi Inari Shrine (landmark)", "Gardens by the Bay (landmark)", "Gateway Arch (landmark)", "Gateway of India (landmark)", "Ghent (city)", "Giant's Causeway (landmark)", "Gibraltar (city)", "Golden Gate Bridge (landmark)", "Grand Canyon (landmark)", "Grand Palace Bangkok (landmark)", "Great Sphinx of Giza (landmark)", "Great Wall of China (landmark)", "Guggenheim Museum Bilbao (landmark)", "Gyeongbokgung Palace (landmark)", "Ha Long Bay (landmark)", "Hallgrimskirkja (landmark)", "Hallstatt (city)", "Hanoi (city)", "Havana (city)", "Hawa Mahal (landmark)", "Helsinki (city)", "Himeji Castle (landmark)", "Hiroshima Peace Memorial (landmark)", "Ho Chi Minh City (city)", "Hobbiton (landmark)", "Hoi An (city)", "Hong Kong (city)", "Honolulu (city)", "Hoover Dam (landmark)", "Horseshoe Bend (landmark)", "Iguazu Falls (landmark)", "India Gate (landmark)", "Jaipur (city)", "Jeju Dol Hareubang (landmark)", "Jodhpur (city)", "Karnak Temple (landmark)", "Kathmandu (city)", "Kinderdijk Windmills (landmark)", "Kinkaku-ji Golden Pavilion (landmark)", "Kotor (city)", "Kraków (city)", "Kronborg Castle (landmark)", "Kyoto (city)", "Lake Bled (landmark)", "Lake Titicaca (landmark)", "Las Lajas Sanctuary (landmark)", "Las Vegas (city)", "Leaning Tower of Pisa (landmark)", "Leshan Giant Buddha (landmark)", "Li River Guilin (landmark)", "Library of Celsus (landmark)", "Lima (city)", "Lincoln Memorial (landmark)", "Lisbon (city)", "Little Mermaid Copenhagen (landmark)", "London (city)", "Los Angeles (city)", "Lotus Temple (landmark)", "Louvre Pyramid (landmark)", "Luang Prabang (city)", "Luxor (city)", "Macau (city)", "Machu Picchu (landmark)", "Manneken Pis (landmark)", "Marina Bay Sands (landmark)", "Matterhorn (landmark)", "Melbourne (city)", "Mesa Verde (landmark)", "Meteora (landmark)", "Mexico City (city)", "Miami (city)", "Milan (city)", "Moai Easter Island (landmark)", "Monaco (city)", "Mont Saint-Michel (landmark)", "Montreal (city)", "Monument Valley (landmark)", "Moscow (city)", "Mostar Bridge (landmark)", "Mount Fuji (landmark)", "Mount Kilimanjaro (landmark)", "Mount Rushmore (landmark)", "Mumbai (city)", "Munich (city)", "Mykonos (city)", "Nazca Lines (landmark)", "Neuschwanstein Castle (landmark)", "New Orleans (city)", "New York (city)", "Niagara Falls (landmark)", "Notre-Dame Cathedral (landmark)", "Nyhavn Copenhagen (landmark)", "Old Faithful Yellowstone (landmark)", "One World Trade Center (landmark)", "Opera Garnier Paris (landmark)", "Oriental Pearl Tower (landmark)", "Osaka (city)", "Osaka Castle (landmark)", "Oslo (city)", "Oxford (city)", "Palace of Versailles (landmark)", "Palenque (landmark)", "Palm Jumeirah (landmark)", "Pamukkale (landmark)", "Paris (city)", "Pena Palace (landmark)", "Perito Moreno Glacier (landmark)", "Persepolis (landmark)", "Petra Treasury (landmark)", "Petronas Towers (landmark)", "Philadelphia (city)", "Pinnacles Desert Australia (landmark)", "Pisa (city)", "Plitvice Lakes (landmark)", "Pompeii (landmark)", "Ponte Vecchio (landmark)", "Pont du Gard (landmark)", "Porto (city)", "Positano (city)", "Potala Palace (landmark)", "Prague (city)", "Prague Castle (landmark)", "Preikestolen (landmark)", "Pyramids of Giza (landmark)", "Quebec City (city)", "Queenstown (city)", "Rainbow Mountain Peru (landmark)", "Reichstag Building Berlin (landmark)", "Reykjavik (city)", "Rialto Bridge (landmark)", "Riga (city)", "Rio de Janeiro (city)", "Rock Churches Lalibela (landmark)", "Roman Forum (landmark)", "Rome (city)", "Ronda Puente Nuevo (landmark)", "Rotterdam (city)", "Sagrada Familia (landmark)", "Salar de Uyuni (landmark)", "Salzburg (city)", "San Francisco (city)", "San Gimignano (city)", "Santorini (city)", "Schönbrunn Palace (landmark)", "Seattle (city)", "Sedona (landmark)", "Senso-ji Temple (landmark)", "Seoul (city)", "Shanghai (city)", "Shirakawa-go (landmark)", "Shwedagon Pagoda (landmark)", "Siena (city)", "Sigiriya (landmark)", "Singapore (city)", "Sistine Chapel (landmark)", "Skellig Michael (landmark)", "Sossusvlei (landmark)", "Space Needle (landmark)", "Spanish Steps (landmark)", "St. Basil's Cathedral (landmark)", "St. Louis (city)", "St. Mark's Basilica Venice (landmark)", "St. Peter's Basilica (landmark)", "St. Petersburg (city)", "Statue of Liberty (landmark)", "Statue of Unity (landmark)", "Stockholm (city)", "Stonehenge (landmark)", "Sugarloaf Mountain Rio (landmark)", "Summer Palace Beijing (landmark)", "Sydney (city)", "Sydney Harbour Bridge (landmark)", "Sydney Opera House (landmark)", "Table Mountain (landmark)", "Tallinn (city)", "Temple of Heaven (landmark)", "Teotihuacan (landmark)", "Terracotta Army (landmark)", "The Bean Chicago (landmark)", "The Gherkin London (landmark)", "The Shard London (landmark)", "Tian Tan Buddha (landmark)", "Tiger's Nest Bhutan (landmark)", "Tikal (landmark)", "Times Square (landmark)", "Todaiji Temple Nara (landmark)", "Tokyo (city)", "Tokyo Skytree (landmark)", "Tokyo Tower (landmark)", "Tori Gate Itsukushima (landmark)", "Toronto (city)", "Torres del Paine (landmark)", "Tower Bridge (landmark)", "Tower of London (landmark)", "Trevi Fountain (landmark)", "Trolltunga (landmark)", "Tulum (landmark)", "Twelve Apostles Australia (landmark)", "US Capitol Building (landmark)", "Udaipur (city)", "Uluru (landmark)", "Valletta (city)", "Valley of the Kings (landmark)", "Valparaíso (city)", "Vancouver (city)", "Varanasi (city)", "Venice (city)", "Victoria Falls (landmark)", "Vienna (city)", "Walt Disney Concert Hall (landmark)", "Warsaw (city)", "Washington D.C. (city)", "Wat Arun (landmark)", "Westminster Abbey (landmark)", "White House (landmark)", "Windsor Castle (landmark)", "Xi'an (city)", "Yosemite National Park (landmark)", "Zhangjiajie Pillars (landmark)"]
```
## Prompts
### Cartoon Style Prompts
```python
# ============================================================
# CARTOON STYLE PROMPTS
# Characteristics: Vibrant, lively, playful/humorous, well-structured
# composition with multiple relevant elements, stylized (not realistic)
# ============================================================

# Public Figures - Cartoon
cartoon_prompt_public_figures = """
Create a Cartoon-Style illustration of "{item}"

CONCEPT:
• Capture their true essence—the depth, significance, and legacy beyond their famous achievements.
• Represent identity through symbolic elements, iconic attributes, or characteristic actions.

STYLE:
• Vibrant, lively colors with playful, expressive energy.
• Well-structured composition integrating relevant symbolic elements.
• Stylized, exaggerated features—NO realistic facial features or photorealistic rendering.
• Include humorous or whimsical touches where appropriate.

FORMAT: 1:1 ratio. No text.
"""

# Film & TV - Cartoon
cartoon_prompt_film_tv = """
Create a Cartoon-Style illustration representing "{item}"

CONCEPT:
• Capture the work's essence—core themes, iconic scenes, or defining atmosphere.
• Depict memorable moments or symbolic compositions that convey its identity.

STYLE:
• Vibrant, lively colors with dynamic, expressive energy.
• Well-structured composition using thematic visual elements.
• Stylized imagery—NO realistic actor/actress portrayals or photorealistic scenes.
• Include playful or whimsical touches where fitting.

FORMAT: 1:1 ratio. No text.
"""

# Literary Works - Cartoon
cartoon_prompt_literary = """
Create a Cartoon-Style illustration representing "{item}"

CONCEPT:
• Capture the essence—central themes, symbolic imagery, or defining atmosphere from the WRITTEN work.
• Depict iconic scenes, key metaphors, or thematic compositions—NOT from film/TV adaptations.

STYLE:
• Vibrant, lively colors with imaginative, expressive energy.
• Well-structured composition integrating literary symbols and motifs.
• Stylized imagery—NO photorealistic rendering or adaptation-derived visuals.
• Include playful or whimsical touches where appropriate.

FORMAT: 1:1 ratio. No text.
"""

# Fictional Characters - Cartoon
cartoon_prompt_fictional = """
Create a Cartoon-Style illustration representing "{item}"

CONCEPT:
• Capture the character through iconic costume, signature accessories, distinctive silhouette, or symbolic elements.
• Convey personality and narrative role through artistic interpretation.

STYLE:
• Vibrant, lively colors with dynamic, expressive energy.
• Well-structured composition with recognizable visual cues (color palette, props, poses, attire).
• Stylized, exaggerated features—NO realistic facial likeness or actor/actress resemblance.
• Include playful or whimsical touches where fitting.

FORMAT: 1:1 ratio. No text.
"""

# Idioms - Cartoon
cartoon_prompt_idioms = """
Create a Cartoon-Style illustration representing the idiom "{item}"

CONCEPT:
• DUAL-LAYER approach: Reference literal wording visually, embedded within a scene conveying figurative meaning.
• Depict a contextual scenario that naturally triggers the idiom's emotional meaning.
• Show clear emotions through exaggerated expressions and body language—avoid pure literal translations.

STYLE:
• Vibrant, lively colors with playful, expressive energy.
• Well-structured composition seamlessly integrating literal and metaphorical elements.
• Stylized cartoon imagery with exaggerated expressions.
• Include humorous touches where appropriate.

FORMAT: 1:1 ratio. No text.
"""

# Places - Cartoon
cartoon_prompt_places = """
Create a Cartoon-Style illustration representing the place "{item}"

CONCEPT:
• Capture unique identity through iconic landmarks, architectural silhouettes, or cultural symbols.
• Incorporate cultural storytelling: local traditions, characteristic energy, or famous associations.

STYLE:
• Vibrant, lively colors with expressive, energetic atmosphere.
• Well-structured composition integrating recognizable visual signatures.
• Stylized, abstracted illustration—NO photorealistic rendering.
• Include playful or whimsical touches where fitting.

FORMAT: 1:1 ratio. No text.
"""

```
### Minimalist Style Prompts

```python

# ============================================================
# MINIMALIST STYLE PROMPTS
# Characteristics: "Less is more", essential elements only,
# pure flat colors (2-3 max), negative space, clean lines
# ============================================================

# Public Figures - Minimalist
minimalist_prompt_public_figures = """
Create a Minimalist-Style illustration of "{item}"

CONCEPT:
• Suggest identity through symbolic abstraction: distinctive silhouette, one iconic attribute, or single signature element.
• Recognition through conceptual association—NOT portrait resemblance.

STYLE:
• Pure, flat colors (2-3 maximum) with clean, simple lines.
• Negative space as primary storytelling tool—emptiness defines form and meaning.
• Stark background: solid color or deliberate emptiness.
• NO realistic facial features, gradients, or complex textures.

FORMAT: 1:1 ratio. No text.
"""

# Film & TV - Minimalist
minimalist_prompt_film_tv = """
Create a Minimalist-Style illustration representing "{item}"

CONCEPT:
• Suggest the work through symbolic abstraction: iconic prop, signature motif, or defining scene reduced to essential geometry.
• Recognition through conceptual association—NOT actor/actress resemblance.

STYLE:
• Pure, flat colors (2-3 maximum) with clean, simple lines.
• Negative space as primary storytelling tool—emptiness suggests narrative weight.
• Stark background: solid color or deliberate emptiness.
• NO realistic portrayals, gradients, or complex textures.

FORMAT: 1:1 ratio. No text.
"""

# Literary Works - Minimalist
minimalist_prompt_literary = """
Create a Minimalist-Style illustration representing "{item}"

CONCEPT:
• Suggest the work through symbolic abstraction: central metaphor, iconic object, or pivotal scene reduced to essential geometry.
• Draw from the WRITTEN work—NOT film/TV adaptations.

STYLE:
• Pure, flat colors (2-3 maximum) with clean, simple lines.
• Negative space as primary storytelling tool—emptiness suggests literary weight.
• Stark background: solid color or deliberate emptiness.
• NO adaptation-derived visuals, gradients, or complex textures.

FORMAT: 1:1 ratio. No text.
"""

# Fictional Characters - Minimalist
minimalist_prompt_fictional = """
Create a Minimalist-Style illustration representing "{item}"

CONCEPT:
• Represent identity through iconic silhouette, signature accessory, or symbolic body language.
• Recognition through visual iconography—NOT facial likeness or actor resemblance.

STYLE:
• Pure, flat colors (2-3 maximum) with clean, simple lines.
• Negative space as primary storytelling tool—emptiness defines presence.
• Stark background: solid color or deliberate emptiness.
• NO realistic facial features, gradients, or complex textures.

FORMAT: 1:1 ratio. No text.
"""

# Idioms - Minimalist
minimalist_prompt_idioms = """
Create a Minimalist-Style illustration representing the idiom "{item}"

CONCEPT:
• DUAL-LAYER approach: Reference literal wording through one essential element, placed in context revealing figurative meaning.
• Use absolute minimum elements—ideally one or two symbolic forms bridging literal and metaphorical.

STYLE:
• Pure, flat colors (2-3 maximum) with clean, simple lines.
• Negative space carries emotional weight—imply context through composition, not detailed scenes.
• Stark background: solid color or deliberate emptiness.
• NO detailed expressions, gradients, or complex textures.

FORMAT: 1:1 ratio. No text.
"""

# Places - Minimalist
minimalist_prompt_places = """
Create a Minimalist-Style illustration representing the place "{item}"

CONCEPT:
• Distill identity into single defining silhouette, architectural form, or cultural symbol.
• Use absolute minimum elements—ideally one iconic shape or two complementary forms.

STYLE:
• Pure, flat colors (2-3 maximum) with clean, simple lines. Colors should reinforce place identity.
• Negative space suggests scale and atmosphere.
• Stark background: solid color or deliberate emptiness.
• NO realistic rendering, architectural detail, gradients, or complex textures.

FORMAT: 1:1 ratio. No text.
"""
```
### MLLM prompts
```python
promptMLLM = {
    "public_figures": """
Identify which public figure the attached image represents.

Instructions:
1. Analyze the visual elements: symbols, attributes, silhouette, color palette, and any iconic features.
2. Consider what these elements suggest about the person's identity, profession, or legacy.
3. Provide your final answer in the last line.

Example:
Input: A cartoon-style image of a woman with blonde hair singing emotionally on stage.
Analysis: The image depicts a blonde woman in an expressive singing pose. The body features and stage presence strongly resemble the British singer Adele, known for her powerful vocals and emotional performances.
Answer: Adele
""",

    "film_tv": """
Identify which film or TV show the attached image represents.

Instructions:
1. Analyze the visual elements: scenes, props, color schemes, symbolic imagery, and thematic motifs.
2. Consider what narrative, genre, or iconic moments these elements suggest.
3. Provide your final answer in the last line.

Example:
Input: A minimalist image showing a red pill and a blue pill against a black background.
Analysis: The image depicts two pills—one red, one blue—a direct reference to the iconic choice scene. This symbolizes the decision between truth and illusion, famously presented in the sci-fi film The Matrix.
Answer: The Matrix
""",

    "literary_works": """
Identify which literary work the attached image represents.

Instructions:
1. Analyze the visual elements: symbols, scenes, objects, color palette, and thematic imagery.
2. Consider what literary themes, narratives, or iconic moments these elements suggest.
3. Provide your final answer in the last line.

Example:
Input: A cartoon-style image of a boy with a lightning bolt scar holding a wand in a castle setting.
Analysis: The image shows a young boy with round glasses and a distinctive lightning bolt scar on his forehead, holding a wand in what appears to be a magical castle. These are iconic elements from J.K. Rowling's fantasy novel series.
Answer: Harry Potter
""",

    "fictional_characters": """
Identify which fictional character the attached image represents.

Instructions:
1. Analyze the visual elements: costume, accessories, silhouette, color scheme, and symbolic attributes.
2. Consider what narrative origin, personality, or iconic traits these elements suggest.
3. Provide your final answer in the last line.

Example:
Input: A minimalist image showing a red cape and an "S" symbol against a blue background.
Analysis: The image features a flowing red cape and the iconic "S" shield emblem, rendered in the classic red and blue color scheme. These are the signature visual elements of the DC Comics superhero known for superhuman strength and flight.
Answer: Superman
""",

    "idioms": """
Identify which idiom or expression the attached image represents.

Instructions:
1. Analyze the visual elements: literal objects, figurative context, emotional cues, and symbolic composition.
2. Consider how literal imagery and figurative meaning are combined to suggest a common expression.
3. Provide your final answer in the last line.

Example:
Input: A cartoon-style image of a person at a podium with butterflies visible in their stomach area.
Analysis: The image shows a nervous speaker at a podium with butterflies illustrated around their midsection. This combines the literal imagery of butterflies with a context of anxiety, representing the feeling of nervousness before a public event.
Answer: Butterflies in stomach
""",

    "places": """
Identify which place (city or landmark) the attached image represents.

Instructions:
1. Analyze the visual elements: architectural forms, landmarks, cultural symbols, and characteristic features.
2. Consider what geographic location or famous site these elements suggest.
3. Provide your final answer in the last line.

Example:
Input: A minimalist image showing an orange silhouette of a bridge with towers against a foggy background.
Analysis: The image depicts the distinctive silhouette of a suspension bridge with two iconic towers, rendered in orange—the signature color of the famous landmark spanning the bay entrance in California.
Answer: Golden Gate Bridge
"""
}

```
## Usage
To generate images for a specific domain and style, format the prompt with the target concept:
```python
# Example usage
concept = "Interstellar (Movie)"
prompt = cartoon_prompt_film_tv.format(item=concept)
print(prompt)

```
