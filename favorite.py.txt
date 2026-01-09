from PIL import Image
import math

def spotlight(image, radius):
    result=image.copy()
    result_pixels=result.load()
    pixels=image.load()
    cx=result.width//2
    cy=result.height//2
    for x in range(result.width):
        for y in range(result.height):
            distance=math.sqrt((x-cx)**2 + (y-cy)**2)
            if distance<=radius:
                result_pixels[x,y]=pixels[x,y]
            else:
                result_pixels[x,y]=0,0,0
    return result

    pass

def animate(image):
    frames=[]
    for i in range(51):
        current_raad=i*(image.width/50)
        frame=spotlight(image, current_raad)
        frames.append(frame)
    return frames
    pass