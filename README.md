bbgame
======
#Create player class with height, average points, rebounds, and name
class bbplayer(object):
    def __init__(self, height, points, rebounds, name):
        self.height = height
        self.points = points
        self.rebounds = rebounds
        self.name = name

    def __str__(self):
        return str(self.name)
#display the player's stats
    def displayStats(self):
        return "%s is %d, averages %d points a game with %d rebounds." % (self.name, self.height, self.points, self.rebounds)
#create a team class made up of 3 players
class Teams(bbplayer):
    def __init__(self, bbplayer1, bbplayer2, bbplayer3, name):
        self.bbplayer1 = bbplayer1
        self.bbplayer2 = bbplayer2
        self.bbplayer3 = bbplayer3
        self.name = name
        
        def __str__(self):
            return str(self.name)
#average the team stats
    def teamstats(self):
         teamHT = (self.bbplayer1.height + self.bbplayer2.height + self.bbplayer3.height)/ 3
         teamPT = (self.bbplayer1.points + self.bbplayer2.points + self.bbplayer3.points)/ 3
         teamRB = (self.bbplayer1.rebounds + self.bbplayer3.rebounds + self.bbplayer3.rebounds)/ 3
         return "the %s average height is %d, average points per game %d and average rebounds are %d." % (self.name, teamHT, teamPT, teamRB)
#total the team points
    def teamTotal(self):
        total = self.bbplayer1.points + self.bbplayer2.points + self.bbplayer3.points
        return total
#find out who the top scorer is
    def rainmaker(self):
        topScore = 0
        total = [self.bbplayer1.points, self.bbplayer2.points, self.bbplayer3.points]
        total.sort()
        topScore += total[2]
        return "The top player scored %d points." % (topScore) 

#create some a bunch of players
tom = bbplayer(510, 13, 2, "Tom")
bob = bbplayer(490, 6, 0, "Bob")
chris = bbplayer(555, 8, 3, "Chris")

brent = bbplayer(510, 32, 9, "Brent")
luke = bbplayer(630, 28, 12, "Luke")
casey = bbplayer(560, 24, 8, "Casey")

rosia = bbplayer(520, 44, 20, "Rosia")
becca = bbplayer(550, 2, 0, "Becca")
christine = bbplayer(570, 4, 1, "Christine")
#create some teams
Knicks = Teams(tom, bob, chris, "Knicks")
Wizards = Teams(brent, luke, casey, "Wizards")
Storm = Teams(rosia, becca, christine, "Storm")

#create a game to find out who the best team is
class games(Teams):
    def __init__(self, team1, team2, name):
        self.team1 = team1
        self.team2 = team2
        self.name = name
        
    def __str__(self):
            return str(self.name)
            
    def score(self):
        a = self.team1.teamTotal()
        b = self.team2.teamTotal()
        c = self.team1
        d = self.team2
        e = self.name
        if a > b:
            return "%s the final score was %d - %d %s wins." % (e, a, b, c)
        else:
            return "%s the final score was %d - %d %s wins." % (e, a, b, d)

#find the top score of the game      
    def topScore(self):
        a = self.team1.rainmaker()
        b = self.team2.rainmaker()
        if a > b:
            return a
        else:
            return b
#create a few games        
game1 = games(Wizards, Nicks, "Wizards - Knicks")
game2 = games(Wizards, Storm, "Wizards - Storm")

#play a few games
print game1.score()
print game1.topScore()
print game2.score()
print game2.topScore()
print Wizards.teamstats()
print brent.displayStats()
