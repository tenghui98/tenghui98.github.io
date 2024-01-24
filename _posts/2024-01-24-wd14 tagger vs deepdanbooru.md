---
title: blip2 vs wd14 tagger vs deepdanbooru
date: 2024-01-24
categories: [image generation]
tags: [image caption]     # TAG names should always be lowercase
---
blip2，wd14 tagger和deepdanbooru 三种image caption方法在动漫图片上的效果对比
- blip2: https://huggingface.co/Salesforce/blip2-opt-2.7b  
- wd14 tagger: https://huggingface.co/SmilingWolf/wd-v1-4-vit-tagger-v2 
- deepdanbooru: https://github.com/KichangKim/DeepDanbooru

### 测试结果
wd14 tagger和deepdanbooru的threshold设置为0.5， 标签按得分降序输出

|  图片   | blip2  |  wd14 tagger   | deepdanbooru  |
|  ----  | ----  |----  | ----  |
| ![1](/assets/2024-01-24/S01E02-00277_center.png) | a man with long hair holding a sword |weapon, 1boy, male focus, sword, solo, topknot, holding, holding weapon, holding sword, fighting stance, brown eyes|sword, weapon, blurry, depth_of_field, katana, blurry_background, holding_sword, 1boy, male_focus, holding_weapon, solo, holding, blurry_foreground, unsheathing, sheath, japanese_clothes, outdoors, long_hair, brown_eyes, topknot, hood, motion_blur, standing|
| ![2](/assets/2024-01-24/S01E02-00517_center.png)  | the character in dynasty warriors 8 has long hair |solo, male focus, 1boy, looking at viewer, brown hair, portrait, brown eyes, parted lips, blurry background, blurry|1girl, solo, blurry, forehead, looking_at_viewer, brown_eyes, face, eyelashes, lips, parted_lips, teeth, realistic|
| ![3](/assets/2024-01-24/S01E10-00649_right.png)  | a demon with red eyes and horns standing in the woods |claws, monster, no humans, horns, glowing, teeth, glowing eyes, sharp teeth, red eyes|sharp_teeth, no_humans, glowing, teeth, spikes, monster, signature, open_mouth, glowing_eyes|
| ![4](/assets/2024-01-24/S01E13-01644_left.png)  | the elder scrolls online - screenshot 3 |scenery, architecture, east asian architecture, tree, no humans, sky, cloud, building, outdoors|architecture, east_asian_architecture, building, city, pagoda, cityscape, scenery, bridge, tower, castle, skyscraper, chimney, sky, gate, cloud, shrine, rooftop, lantern, tree, skyline, house, railing, no_humans, clock_tower, water, stairs, arch, city_lights, fantasy, outdoors, library, cloudy_sky, paper_lantern, town|
| ![5](/assets/2024-01-24/S01E23-01742_left.png)  | the legend of china is coming to the west |weapon, sword, armor, fire, multiple boys, 2boys|fire, red_sky, sunset, orange_sky, embers, twilight, weapon, dusk, sword, burning, evening, molten_rock, east_asian_architecture, red_moon, gradient_sky, architecture, pagoda, building, male_focus, sky, flame, castle, cityscape, bridge, armor, 1boy, autumn, fireplace, solo, cloud, samurai, katana, tree, mountain, explosion, autumn_leaves, facial_hair, standing, purple_sky, outdoors, planted, torii, japanese_clothes, planted_sword, holding, holding_sword, sun, flaming_weapon, city, red_theme|

结果对比中可以看出：  
- blip2是对图片主体事物的直观一句话描述，缺少细节的描述。对于某些图片会产生幻觉，产生人类无法理解的奇怪描述。  
- deepdanbooru产生的描述比wd14-tagger更丰富，但有不少标签存在重复和与图片关联性不强的问题。  
- blip2对性别理解的准确率优于另外两种方法。deepdanbooru和wd14-tagger常常boy girl不分。(似乎头发长就是girl？)  
