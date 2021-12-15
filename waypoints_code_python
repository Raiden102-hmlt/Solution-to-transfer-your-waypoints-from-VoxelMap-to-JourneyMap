waypoints_text = '''[your waypoints]'''         #Change here
directory = '[your destination folder]'         #Change here too

N = 1                   #Initialized at 1 because it counts the number of returns : "\n", if there is only 1 waypoint it would be outputting 0
for i in waypoints_text:         #Counts the number of waypoints
    if i == "\n":
        N+=1

def replace(string, old, new):    #Replaces text in a string
    for k in range(len(string)):
        if string[k:k + len(old)] == old:
            if k == 0:
                string = new + string[k + len(old):]
            elif k == len(string) - (len(old)-1):
                string = string[:k] + new
            else:
                string = string[:k] + new + string[k + len(old):]
    return string

chain0 = replace(waypoints_text,"name:","")     #Removes useless text bothering further instructions
chain1 = replace(chain0,"x:","")        #Also delete the "x:" part of "suffix:" but it doesn't matter
chain2 = replace(chain1,"y:","")
chain3 = replace(chain2,"z:","")
chain4 = replace(chain3,"enabled:","")
chain5 = replace(chain4,"red:","")
chain6 = replace(chain5,"green:","")
chain7 = replace(chain6,"blue:","")
chain = replace(chain7,"dimensions:","")

split_chain = chain.split("\n")     #Separates all waypoints lines and puts them all in a single list
# print(split_chain)

list_of_waypoints = []
dimensions = []
for i in range(N):                  
    waypoint = split_chain[i].split(",")    #Separates each waypoint line...
    list_of_waypoints.append(waypoint)      #...and puts them in a sub-list
    del list_of_waypoints[i][8] #Removes useless info once again
    del list_of_waypoints[i][8] #Same index as before because once removed, the old n°9 will be a new n°8
    list_of_waypoints[i][5] = int(float(list_of_waypoints[i][5])*255)   #In voxel, colours values are between 0 and 1, in journeymap bewteen 0 and 255, so it just converts them
    list_of_waypoints[i][6] = int(float(list_of_waypoints[i][6])*255)
    list_of_waypoints[i][7] = int(float(list_of_waypoints[i][7])*255)
    dimensions.append(list_of_waypoints[i][8].split("#"))   #Separates the dimensions in a list
    del dimensions[i][-1]  #Because of the format of the dimensions, there is a parasite item in last place


import os
for i in range (N):
    id = str(list_of_waypoints[i][0]) + "_" + str(list_of_waypoints[i][1]) + "," + str(list_of_waypoints[i][3]) + "," + str(list_of_waypoints[i][2])
    filename = id + ".json"
    fullname = os.path.join(directory, filename)
    f = open(fullname, "a")
    f.write("{\n  @id@: @")     #Writes in the files the necessary information along with the needed format
    f.write(id)
    f.write("@,\n  @name@: @")  #I use @ instead of " when working with the file because it won't interfere with it in unwanted evident ways
    f.write(str(list_of_waypoints[i][0]))
    f.write("@,\n  @icon@: @waypoint-normal.png@,\n  @x@: ")
    f.write(str(list_of_waypoints[i][1]))
    f.write(",\n  @y@: ")
    f.write(str(list_of_waypoints[i][3]))   #No mistake, the height is Y in journeymap...
    f.write(",\n  @z@: ")
    f.write(str(list_of_waypoints[i][2]))
    f.write(",\n  @r@: ")
    f.write(str(list_of_waypoints[i][5]))
    f.write(",\n  @g@: ")
    f.write(str(list_of_waypoints[i][6]))
    f.write(",\n  @b@: ")
    f.write(str(list_of_waypoints[i][7]))
    f.write(",\n  @enable@: ")
    f.write(str(list_of_waypoints[i][4]))
    f.write(",\n  @type@: @Normal@,\n  @origin@: @journeymap@,\n  @dimensions@: [\n    @")
    for j in range(len(dimensions)):
        if len(dimensions[i]) > 1:    #Because the last dimension mentionned has to be followed by a coma I have to make this
            f.write(dimensions[i][0])
            del dimensions[i][0]
            f.write("@,\n    @")
        elif len(dimensions[i]) == 1:
            f.write(dimensions[i][0])
            del dimensions[i][0]
            f.write("@\n  ],\n  @persistent@: true\n}")
    f.close()
    with open(fullname) as r:     #I used @ to be " and now i'm replacing them again
        text = r.read().replace('@', '"')
    with open(fullname
              , "w") as w:
        w.write(text)
    f.close()
