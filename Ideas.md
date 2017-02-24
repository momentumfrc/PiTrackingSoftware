#Euvin's Ideas
*This is the text document Euvin created at the last meeting with his ideas on how to improve the vision processing*

get each blob from all blobs
compare the current one to all blobs left in a loop
select all blobs that have similar width and similar height (basically check for similar shape, which getarea cannot gaurantee)

```
//similarBlobs is an array of blobs
for each blob (Compare1) in allBlobs{
	if similarBlobs.size() <= 1 { //only changes Compare1 if there are no matching blobs found (yet)
		similarBlobs[0] = Compare1;
		for each blob (Compare2) in allBlobs{
			//compare width and height
			//if a match is found, add to SimilarBlobs

			similarBlobs.add(Compare2);
		}
	}else{
		break; //breaks loop if matches were found already
	}
}

double distanceFactor = 3 //This would be assuming that the distance between the two blobs is 3 times their average width
double pairDistanceThreshold = 5 //because life isn't perfect
boolean foundPair = false
if similarBlobs.size() > 1 { //if matches were found
	for each blob (Compare1) in similarblobs{
		if foundPair {
			for each blob (Compare2) in similarblobs{
				//then compare the distance between Compare1 and Compare2
				//if the distance is found to be acceptable, break the loop and place the crosshairs

				avgBlobWidth = (Compare1.getWidth() + Compare2.getWidth()) / 2
				distanceError = abs((distanceFactor*avgBlobWidth)-distance)
				if (distanceError < pairDistanceThreshold) {
					foundPair = true;
					//set to true to prevent further looping
					//sets crosshair to be inbetween them
					crosshairX = (Compare1.centerX() + Compare2.centerX())/2;
					crosshairY = (Compare1.centerY() + Compare2.centerY())/2;
				}
			}
		}else{
			break;
		}
	}
}
```
