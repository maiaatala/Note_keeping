<style>
    img{
        width: 200px;
        height: auto;
        object-fit: cover;
    };
</style>

# Imagens.

- [Imagens.](#imagens)
  - [When was the first case of an image being stored ?](#when-was-the-first-case-of-an-image-being-stored-)
  - [How are images stored?](#how-are-images-stored)
    - [Colors](#colors)
      - [Indexed Colors](#indexed-colors)
      - [RGB](#rgb)
      - [HEX](#hex)
      - [The 32 bit image](#the-32-bit-image)


## When was the first case of an image being stored ?
<img src="https://upload.wikimedia.org/wikipedia/commons/1/1a/NBSFirstScanImage.jpg" alt="first picutre" />

The history of digital photography as we know it began in the 1950s. In 1951, the first digital signals were saved to magnetic tape via the first video tape recorder. Six years later, in **1957**, the first digital image was produced through a computer by *Russell Kirsch*. It was an image of his son.

A picture of Kirsch's three-month-old son, was captured as just 30,976 pixels, a 176 × 176 array, in an area 5 cm × 5 cm (2" x 2"). The bit depth was only one bit per pixel, stark black and white with no intermediate shades of gray, but, by combining several scans made using different scanning thresholds, grayscale information could also be acquired

<img src="https://madeupinbritain.uk/britimages/TompsettColourPicture.jpg" alt="first picutre" />

The first published color digital photograph was produced in 1972 by Michael Francis Tompsett using CCD sensor technology and was featured on the cover of Electronics Magazine. It was a picture of his wife, Margaret Thompsett.

An important development in digital image compression technology was the [**discrete cosine transform**](https://en.wikipedia.org/wiki/Discrete_cosine_transform) (DCT), a lossy compression technique first proposed by Nasir Ahmed while he was working at the Kansas State University in 1972. DCT compression is used in JPEG image standard, which was introduced by the [*Joint Photographic Experts Group*](https://en.wikipedia.org/wiki/Joint_Photographic_Experts_Group) in 1992. JPEG compresses images down to much smaller file sizes, and has become the most widely used image file format.[14] The JPEG standard was largely responsible for popularizing digital photography.

<img src="https://static.bhphotovideo.com/explora/sites/default/files/samsung-sch-v200.jpg" alt="Samsung SCH-V200" >
<img src="https://static.bhphotovideo.com/explora/sites/default/files/item34.jpg" alt="Sharp Electronics J-SH04 J-Phone" />

The first cell phones with built-in digital cameras were produced in 2000 by Sharp and Samsung. Small, convenient, and easy to use, camera phones have made digital photography ubiquitous in the daily life of the general public. 

[via](https://en.wikipedia.org/wiki/Digital_photography#History)

## How are images stored?

an image is stored as a 2 dimentional array

the basic information needed in every image file format (Metadata):
- Start block
- End block
- Resolution (Height & Width)
- Pixel density
- Colour Depth
- Extra information
  - Date taken
  - Device taken from
  - Author
  - Comments
  - etc.

The image must be broken down into tiny elements called PIXELS (short for Pixel Element). For every pixel, an average color is found and a binry value is assigned. an image with a resolution of 1024 x 798 pixels has 1024*798 = 817,152 pixels total. 

Each pixel is then represented by a binary value of its color, the size of this value is called *Colour Depth*. therefore, the size of an image is, at least its W * H * Colour Depth

An image with W = 4928 pixels, H = 3264 pixels and a colour depth of 24 bits/pixel becomes:
4928 * 3264 * 24 => 386,039,808 bits / 8bits/1 byte => 48,254,976 bytes => 48 MB

### Colors

bits | example 1 | example 2 | example 3
--- | --- | --- | ---
1 bit | <img src="https://i.ytimg.com/vi/aqseu63_8wY/maxresdefault.jpg" /> | <img src="https://i.pinimg.com/474x/69/ee/32/69ee3235137b5ec09d880922da0bfc85.jpg" />  | <img src="https://i.pinimg.com/originals/db/03/1f/db031fa79da1c2549c30e64d0786ba37.png" />
2 bit | <img src="https://cdn.dribbble.com/users/626374/screenshots/14544338/dribbble_still.gif?compress=1&resize=400x300" /> | <img src="https://res.cloudinary.com/teepublic/image/private/s--uypz7yeY--/t_Resized%20Artwork/c_fit,g_north_west,h_1054,w_1054/co_ffffff,e_outline:53/co_ffffff,e_outline:inner_fill:53/co_bbbbbb,e_outline:3:1000/c_mpad,g_center,h_1260,w_1260/b_rgb:eeeeee/t_watermark_lock/c_limit,f_auto,h_630,q_90,w_630/v1608153756/production/designs/17469924_0.jpg" />  | <img src="https://img.itch.zone/aW1nLzIyMDQxMTYucG5n/original/7URm1o.png" />
8 bit | <img src="https://i.pinimg.com/originals/4c/f5/83/4cf58303bb1aa59e2ccadc63e0bd4785.gif" /> | <img src="https://bojoga.com.br/files/2009/12/Metroid.jpg" />  | <img src="https://d23gn3985hkc32.cloudfront.net/wp-content/uploads/2020/12/308097-Capture14.png" />
16 bit | <img src="https://2.bp.blogspot.com/_vAxLnr-8Y7E/TNcNK7cTTtI/AAAAAAAAAVU/Q-e0ySPwuZw/s1600/casa.jpg" /> | <img src="https://i2-prod.mirror.co.uk/incoming/article7539059.ece/ALTERNATES/s1200b/Stardew-hi-res.jpg" />  | <img src="https://gamefabrique.com/screenshots2/snes/mega-man-x-17.big.jpg" />
32 bit | <img src="https://www.derekyu.com/makegames/images/pixel/orc07.png" /> | <img src="https://pbs.twimg.com/media/DorNP3YXoAAwRTD?format=jpg&name=large" />  | <img src="https://pbs.twimg.com/media/DorNRE6XsAAwaxg?format=jpg&name=large" />


#### Indexed Colors

We could, for small colored images, pass with the image it's pallet, which would yield something similar to:
binary | color
--- | ---
00 | white
01 | black
02 | green
03 | dark green

adding another binary will double the number of colours available:
colour depth | binary | n of possibilities
--- | --- | ---
1 bit | 0 - 1| 2
2 bit | 00 - 11| 4
3 bit | 000 - 111 | 8
8 bit | 00000000 - 11111111 | 256
16 bit | 00000000 00000000 - 11111111 11111111 | 65.536
24 bit | 00000000 00000000 00000000 - 11111111 11111111 11111111 | 16.777.216 
32 bit | 00000000 00000000 00000000 00000000 - 11111111 11111111 11111111 11111111 | 4.294.967.296

#### RGB

<img src="https://pages.cms.hu-berlin.de/EOL/geo_rs/fig/s02_addcolor_rgbscreen.png">

The RGB color modal is an *addictive color model* in which red, green and blue primary colors of light are added together in various ways to reproduce a broad array of colors
the way it works in the computer is: **24 bits will be reserved PER PIXEL, in which each byte represents a color in the RGB system.**

Therefore we actually have 3 different images stored in the computer, one which is only red, one that is only green and another that is only blue, and in the end, the computer will merge all 3 together to create the final colored image

<img src="https://res.cloudinary.com/practicaldev/image/fetch/s--7uHGwEG8--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://i.ibb.co/HgnybWG/rgb.png">

<img src="https://cdn.analyticsvidhya.com/wp-content/uploads/2021/03/Screenshot-from-2021-03-16-11-01-53.png">

#### HEX

The Hex triplet is a six-digt three-byte hexadecimal number used in HTML, CSS, SVG to represente the RGB colors. one byte represents a number in grange 00 to FF in hexadecimal, or 0 to 255 in decimal

For example, consider the color where the red/green/blue values are decimal numbers: red=36, green=104, blue=160 (a grayish-blue color). The decimal numbers 36, 104, and 160 are equivalent to the hexadecimal numbers 24, 68, and A0 respectively. The hex triplet is obtained by concatenating the six hexadecimal digits together, 2468A0 in this example. 

[via](https://en.wikipedia.org/wiki/Web_colors#Hex_triplet)

color | hex | rgb
--- | --- | ---
deep pink | FF 14 93 | 255 20 147
yellow | FF FF 00 | 255 255 0
cyan | 00 FF FF | 0 255 255
royal Blue | 41 69 E1 | 65 105 225


#### The 32 bit image

in most cases, when we refer to a 32 bit images, what we mean is, the 24 standart color representation of RGB plus an **alpha channel**, meaning, the bit's transparency



https://www.bbc.co.uk/bitesize/guides/zpfdwmn/revision/2
https://alekya3.medium.com/how-images-are-stored-in-a-computer-f364d11b4e93
https://codeburst.io/how-are-images-stored-on-a-computer-353ac16b6d8f