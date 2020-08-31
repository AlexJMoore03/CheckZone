#py Desktop\code\Turret.py

import math

#Calculates dot product
def dot(x, y):
    return sum(xi * yi for xi, yi in zip(x, y))

def checkZone(originPointX, originPointY, originPointZ, directionVectorX, directionVectorY, directionVectorZ, checkPointX, checkPointY, checkPointZ, angle, distance):
    #Special case where origin and check are equal
    if originPointX == checkPointX and originPointY == checkPointY and originPointZ == checkPointZ:
        return True
    #Gets the distance from the originPoint to the checkPoint  with the distance formula
    hypotenuseLength = math.sqrt(((checkPointX-originPointX)**2) + ((checkPointY-originPointY)**2) + ((checkPointZ-originPointZ)**2))
    #Checks if the distance from the originPoint to the checkPoint is within the provided distance
    if hypotenuseLength <= distance:
        #Defines the values that will be necessary to calculate the distance from the checkPoint to the closest point on the ray
        originToCheckArray = [originPointX - checkPointX, originPointY - checkPointY, originPointZ - checkPointZ]
        directionVectorArray = [directionVectorX, directionVectorY, directionVectorZ]
        directionVectorMagnitude = math.sqrt((directionVectorX**2) + (directionVectorY**2) + (directionVectorZ**2))
        #Calculates the aforementioned distance using the distance from point to line in space formula
        oppositeLength = math.sqrt((hypotenuseLength**2) - (((dot(originToCheckArray, directionVectorArray)) / (directionVectorMagnitude**2))**2))
        #Returns radians
        interiorAngle = math.asin(oppositeLength / hypotenuseLength)
        #Checks if the angle between the direction vector and the checkPoint (multiplied by 2 to account for the angle mirrored across the direction vector) is within the provided angle (converted to radians)
        #This condition will be true if the point is within the intended angle, or a 180 degree mirror of it
        if interiorAngle * 2 <= math.radians(angle):
            rayPointX = originPointX + directionVectorX
            rayPointY = originPointY + directionVectorY
            rayPointZ = originPointZ + directionVectorZ
            oppositePointX = originPointX - directionVectorX
            oppositePointY = originPointY - directionVectorY
            oppositePointZ = originPointZ - directionVectorZ
            intendedDistance = math.sqrt(((checkPointX-rayPointX)**2) + ((checkPointY-rayPointY)**2) + ((checkPointZ-rayPointZ)**2))
            oppositeDistance = math.sqrt(((checkPointX-oppositePointX)**2) + ((checkPointY-oppositePointY)**2) + ((checkPointZ-oppositePointZ)**2))
            #Checks if the checkPoint is closer to the opposite of the directionVector, meaning it is in the mirror of the intended angle instead of the actual one
            if oppositeDistance < intendedDistance:
                #Special case where the point is not within the space left on the side opposite the direction
                if (interiorAngle) * 2 >= 6.283185307 - math.radians(angle):
                    return True
                return False
            return True
    return False
        
#originPoint: The point the ray begins from
#directionVector: The direction of the ray
#checkPoint: The point to check if meets the paramters
originPointX_ = input("Point of Origin (X): ")
originPointY_ = input("Point of Origin (Y): ")
originPointZ_ = input("Point of Origin (Z): ")
directionVectorX_ = input("Direction Vector (X): ")
directionVectorY_ = input("Direction Vector (Y): ")
directionVectorZ_ = input("Direction Vector (Z): ")
checkPointX_ = input("Point to Check (X): ")
checkPointY_ = input("Point to Check (Y): ")
checkPointZ_ = input("Point to Check (Z): ")
angle_ = input("Angle (Degrees): ")
distance_ = input("Distance: ")

print(checkZone(float(originPointX_), float(originPointY_), float(originPointZ_), float(directionVectorX_), float(directionVectorY_), float(directionVectorZ_), float(checkPointX_), float(checkPointY_), float(checkPointZ_), float(angle_), float(distance_)))
