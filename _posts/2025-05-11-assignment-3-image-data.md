---
title: "Assignment 3 - Image Data"
categories:
  - Assignments
  - Blog
tags:
  - Assignments
  - Orange
  - Images
  - 2DCLIP
  - Distant Viewing
---

# Image Data and Vintage Brazilian Packaging

In assignment 3, I investigate how neural networks interpret vintage Brazilian packaging designs. Using Orange Data Mining, 2DCLIP, and DV Explorer, I analyzed 75 images of Brazilian product packaging, ranging from tobacco and snacks to drinks and amusement park cards, exploring the tensions between algorithmic vision and cultural interpretation. What follows is a critical reflection on this process, tracing how computational tools attempt to interpret cultural meaning, and how, in the words of Impett and Offert, "in reading a corpus of visual culture through a neural network, we are always also doing the reverse."

## Corpus Construction: Navigating Brazilian Visual Heritage

The initial process began with selecting a domain that fit the assignment requirements: avoiding faces while exploring culturally rich imagery outside common AI training sets. After considering movie posters (too many faces), currency (too common in datasets), and other possible topics, I settled on vintage Brazilian packaging designs, a form of art rich in typography, color, and culture, which I grew up with. My collection process combined manual curation with semi-automated tools. Using Pinterest boards, Tumblr archives (lugaresinexistentes.tumblr.com), e-commerce sites (casadovelho.com.br), and design archives (The Dieline), I gathered a diverse corpus spanning several decades of Brazilian consumer culture. Although the Chrome extension "Imageye" made the process slightly faster, most of it ended up being manual work.

Categorization posed the first analytical challenge. I began with product-based categories (cards, drinks, snacks, tobacco), but encountered single instances such as butter, cheese, paper clips, and vinegar, which led to the creation of an “Other” category. My main categorization resulted in following five core groups:

## Main Categories

1.  Cards: Carnival park tickets, bank cards (e.g., Playland, Banco Bradesco)
    
2.  Drinks: Alcoholic (cachaça, beer) and non-alcoholic (guaraná, milk) labels
    
3.  Snacks: Chocolate bars (e.g., Lacta), chewing gum, biscuits
    
4.  Tobacco: Cigarette packs (Sabrati, Calypso)
    
5.  Other: butter, cheese, paper clips, vinegar, perfume

This structure grounded the corpus in tangible product types but struggled with outliers. For example, a Cinzano perfume bottle or Chispazo matchbox didn’t fit into existing groups, necessitating the "Other" category.

Alternative Classification Systems

For computational analysis (Parts 2-3 of the assignment), I developed three new category systems to test algorithmic perception:

1.  Color Dominance (Cool vs. Warm)
-   Cool: Blues, greens, muted tones (e.g., Cinzano perfume’s teal background)
-   Warm: Reds, yellows, oranges (e.g., Piranha cachaça’s crimson label)
    
3.  Cultural Symbolism (Neutral vs. Tropical vs. Urban)
-   Neutral: Text-heavy/minimalist designs (e.g., bank cards, matchboxes)
-   Tropical: Nature and rural motifs (palms, fruits), bright colors
-   Urban: Geometric patterns, modern typography, urban architecture motifs

5.  Design Era (Vintage vs. Modern)
-   Vintage: Pre-2000s designs (ornate borders, serif fonts)
-   Modern: Post-2000s (minimalist logos, flat colors)

## Clustering: Machine Vision vs. Cultural Meaning

Orange Data Mining's workflow for unsupervised exploration began with importing images and generating Inception-v3 embeddings. The resulting visualizations revealed how algorithms group images by visual similarity rather than cultural function.

Image grid
![Annotated Image Grid](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Image%20Grid%201%20(Resize).png)

Annotated image grid
![Annotated Image Grid](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Image%20Grid%202%20-%20Annotated.png)

The annotated image grid divides into four quadrants, each revealing how machine vision prioritizes formal qualities over cultural context:

-   Top-Left (Rectangular Formats & Text-Heavy Designs): Cluster with tobacco packaging despite their different cultural roles, linked by their rectangular format and typographic emphasis.
    
-   Top-Right (Bright Colors & Brand-Focused Layouts): Colorful drink labels with strong logo presence group together based on circular shapes and saturated colors, regardless of era or beverage type.
    
-   Bottom-Left (Vintage Typography & Packaging): Tobacco products and snacks with muted, nostalgic color palettes cluster based on shared aesthetic qualities rather than function.
    
-   Bottom-Right (Vibrant Product Photography): Drink bottles with photographic elements and contemporary designs show the algorithm's sensitivity to modern visual language.

Hierarchical Clustering Dendrogram
![Hierarchical Clustering Dendrogram](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Clustering%20-%20Inception-v3%20(Ward).png)

Clustering example 1
![Clustering example 1](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Clustering%201.png)

![Clustering example 1](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Clustering%202%20(Image%20Viewer).png)

Clustering example 2
![Clustering example 2](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Clustering%202.png)

![Clustering example 2](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Clustering%202%20(Image%20Viewer).png)

Clustering example 3
![Clustering example 3](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Clustering%203.png)

![Clustering example 3](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Clustering%203%20(Image%20Viewer).png)

The dendrogram visualization further revealed how algorithms organize visual culture. Cards formed a tight cluster based on uniform layout, while drinks and snacks mixed based on shared visual traits. For example, a 1970s cachaça label might group with a 1990s chocolate bar due to similar color schemes, despite their distinct cultural contexts. This pattern exemplifies what Impett and Offert call "reverse reading", the classifications tell us more about how Inception-v3 was trained on Western datasets than about Brazilian visual culture itself. The model's "vision" is shaped by ImageNet's biases, not by Brazilian design history.

## Classification: Testing the Algorithm's Cultural Literacy

To examine how well algorithms predict human categories, I created three classification systems, each testing different aspects of cultural understanding:

## System 1: Color Dominance (Warm vs. Cool)

In the color dominance classification, I manually assigned each image to either the "warm" or "cool" category based on my own visual judgment of the dominant color palette. For example, the Cinzano perfume box was categorized as "warm" because, despite its teal background, the gold and red accents visually dominated the design and gave it a warmer impression. This manual labeling served as the ground truth for the algorithm's supervised learning task in Orange.

The algorithm then attempted to predict these human-assigned categories using image embeddings. As shown in the screenshot, the majority of images were correctly classified, but some misclassifications occurred. These misclassifications often happened with images that contained both warm and cool elements or where the dominant color was ambiguous. For instance, some packaging with a mix of green and red could be interpreted differently by the algorithm, depending on how it weighted color regions.

This process highlighted that while my own classification was influenced by cultural associations and overall visual impression, the algorithm relied purely on pixel-level color distributions. As a result, the model sometimes disagreed with my judgment, revealing the gap between human perception (which can be context-sensitive and holistic) and computational perception (which is statistical and local).

Confusion Matrix (correct)
![Color dominance](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Color%20Dominance%20-%20Confusion%20Matrix%20(Correct).png)

Confusion Matrix (misclassified)
![Color dominance](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Color%20Dominance%20-%20Confusion%20Matrix%20(Misclassified).png)

Caption: Confusion matrix showing the algorithm’s predictions for “warm” and “cool” categories based on my manual assignments. Most images are correctly classified, but ambiguous or mixed-color designs present challenges for both human and machine.

## System 2: Cultural Symbolism (Tropical vs. Urban vs. Neutral)

This classification system was designed to probe the algorithm’s ability to recognize and distinguish between different layers of Brazilian cultural symbolism as expressed in packaging design. The process began with a conceptual debate: should “rural” imagery such as farm scenes, agricultural motifs, and references to Brazil’s countryside be given its own category, or should it be merged with “tropical,” which already encompassed nature, fruits, and lush color palettes? After reviewing the distribution of images and reflecting on Brazilian cultural identity, I decided to merge rural with tropical. This was both a practical and conceptual choice: it balanced the number of images per category and acknowledged the connection between rural and tropical imagery in Brazil’s national narrative.

The final categories were:

-   Tropical: Packaging featuring nature, fruits, plants, and bright, lush colors.
-   Urban: Designs with geometric patterns, modern typography, and references to city life or industrial aesthetics.
-   Neutral: Text-heavy, minimalist, or ambiguous designs that did not strongly evoke either tropical or urban themes.

Image grid
![Cultural Symbolism](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Cultural%20Symbolism%20-%20Image%20Grid%201%20(Crop).png)

The image grid visualization reveals how these categories played out visually. “Tropical” images, often rich in greens, yellows, and illustrations of fruit or animals, tended to cluster together. “Neutral” designs, dominated by text or minimalist layouts, were scattered across the grid, sometimes bordering both tropical and urban clusters. “Urban” images, while fewer, appeared in pockets where modernist or geometric design elements were prominent.

When I ran the supervised classification in Orange, the model achieved an overall accuracy of 64%, with the “urban” category performing the worst (58% accuracy). The confusion matrices illustrate where the model succeeded and struggled. Most notably, the algorithm often confused “urban” and “neutral” images. For example, packaging with bold, modern fonts but little visual context could be interpreted as either urban (due to typography) or neutral (due to the absence of explicit urban motifs). Similarly, some “tropical” images with less saturated colors or more abstract representations of nature were misclassified as neutral.

Confusion Matrix (correct)
![Cultural Symbolism](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Cultural%20Symbolism%20-%20Confusion%20Matrix%20(Correct).png)

Confusion Matrix (misclassified)
![Cultural Symbolism](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Cultural%20Symbolism%20-%20Confusion%20Matrix%20(Misclassified).png)

On one hand, the algorithm was quite successful at grouping overtly tropical imagery, showing sensitivity to color and illustration style. On the other, it struggled with the more ambiguous or hybrid designs, precisely those that, for a human with cultural context, might be the most interesting. The “neutral” category, while methodologically useful, also became a kind of “miscellaneous” group for images that defied easy classification, which may have contributed to the model’s confusion.

System 3: Design Era (Vintage vs. Modern)

For the Design Era system, I manually classified the corpus into "Vintage" and "Modern" categories based on my judgment of each image's design aesthetic, resulting in 62 vintage and 13 modern images. This imbalance reflected both the actual prevalence of vintage designs in my collected corpus and my subjective decisions about what constituted "vintage" versus "modern" aesthetics.

The algorithm then attempted to learn from these human-assigned labels. When analyzing misclassifications, I noticed cases where the algorithm struggled to match my classifications for items with mixed or ambiguous temporal design cues. For example, 2010s designs with retro-inspired typography that I had labeled as "modern" based on my knowledge of their actual production date were sometimes predicted as "vintage" by the algorithm, which could only react to visual cues rather than historical knowledge.

Reflecting on these results, we can conclude that the process of labeling and categorizing was itself an interpretive act shaped by my own understanding of Brazilian culture and design history. The algorithm, by contrast, operated strictly on visual features, with no access to the cultural or historical context that informed my decisions. This gap between human and machine judgment became especially apparent in edge cases: for example, a minimalist label for a traditional Brazilian product might be seen as “neutral” by the algorithm, but as “tropical” by a human familiar with the brand’s legacy.

Image Grid
![Design Era](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Design%20Era%20-%20Image%20Grid%201%20(Crop).png)

Confusion Matrix (correct)
![Design Era](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Design%20Era%20-%20Confusion%20Matrix%20(Correct).png)

Confusion Matrix (misclassified)
![Design Era](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Design%20Era%20-%20Confusion%20Matrix%20(Misclassified).png)

## Multimodal Models: CLIP's Cultural Flatness

The 2DCLIP tool allowed mapping each image in a 2D space where the horizontal axis represents "Vintage" and the vertical axis represents "Modern." Rather than simply arranging images in a diagonal line (which would indicate these concepts are perfect opposites). This visualization revealed some insights:

-   Temporal Ambiguity: Many images cluster in the middle, suggesting CLIP sees them as having mixed vintage and modern characteristics.

-   Visual Markers of Era: The upper portion contains mostly minimalist designs and cards with clean layouts, which CLIP associates strongly with "Modern" regardless of their actual production date.

2DCLIP
![Vintage and Modern](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/2DCLIP%20-%20Vintage%20vs%20Modern.png)

DV Explorer's image captions also resulted in some interesting results, but mostly because of how nonsensical they tended to be:

-   A Piranha cachaça label, featuring a stylized red piranha (an Amazonian fish central to Brazilian folklore), was described as "a book with a picture of a dog on it."
    
-   A Cinzano perfume bottle became "a bottle of booze on a table" (when no table was present).
    
-   A Skol beer was labeled generically as "a beer bottle with a beer in it". Accurate, but described in a peculiar way.

![Image caption](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/image%20caption%20(12).png)

![Image caption](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/image%20caption%20(11).png)

![Image caption](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/image%20caption%20(1).png)

![Image caption](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/image%20caption%20(13).png)

![Image caption](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/image%20caption%20(3).png)

![Image caption](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/image%20caption%20(5).png)

![Image caption](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/image%20caption%20(7).png)

These failures exemplify Impett and Offert's concept of "reverse reading", the model's outputs reveal its training on Anglophone data and Western visual conventions, not the cultural realities of Brazilian design.

## The Limits of Computational Vision

This assignment revealed two major blind spots in algorithmic interpretation of cultural artifacts:

1.  Temporal Collapse: Retro-modern designs blurred with genuine vintage items, erasing Brazil's complex design evolution and nostalgic revivals.
    
2.  Linguistic Blindness: Portuguese typography was treated as decorative texture rather than meaningful text.

As Arnold and Tilton argue in Distant Viewing, computational methods must be accompanied by critical human interpretation. This assignment demonstrated that every algorithmic classification required human contextualization to avoid cultural flattening. The Orange workflow itself represents this connection between computation and interpretation, between distant and close viewing.

Orange workflow
![Orange workflow](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/Image%20Data/Process/Orange.png)

## Conclusion

This process of analyzing Brazilian visual culture via algorithmic interpretation revealed computational vision as simultaneously powerful and limited. Tools like Orange and CLIP detect patterns humans might miss, but it also misses the cultural and historical dimensions that give these objects meaning. The most valuable insight came not from what the algorithms correctly identified, but from what they misunderstood. When a cachaça label becomes "a book with a dog," we learn how machine vision fails to recognize typical images that it might not be trained upon, flattening differences into familiar categories. This "reverse reading" of neural networks reveals the biases embedded in their training data and architecture.

Therefore, we must approach computational tools not as neutral instruments, but as culturally situated actors. When algorithms analyze Brazilian design, they translate between cultural frameworks, often losing crucial context in the process. Future work might integrate culturally specific training data, incorporate metadata on historical context, or develop hybrid methods that balance computational pattern recognition with local cultural knowledge. Nonetheless, computational analysis of cultural artifacts will always require reflexive awareness of how algorithms "see" differently than humans embedded in specific cultural traditions.

## Google Drive with all of the pictures:

[Google Drive](https://drive.google.com/drive/folders/1LPu8nnRGknsNtkdGq_kow03iPMH_0qDy?usp=drive_link)

<iframe src="https://drive.google.com/embeddedfolderview?id=1LPu8nnRGknsNtkdGq_kow03iPMH_0qDy#grid" style="width:100%; height:600px; border:0;"></iframe>

## References

Arnold, T., & Tilton, L. (2023). Distant Viewing: Computational Exploration of Digital Images. MIT Press.  
[https://mitpress.mit.edu/9780262546133/distant-viewing/]

Impett, L., & Offert, F. (2024). “In reading a corpus of visual culture through a neural network, we are always also doing the reverse.” In Distant Viewing: Computational Exploration of Digital Images (Arnold & Tilton, Eds.).

2DCLIP  
Impett, L. (n.d.). 2DCLIP. Retrieved from [https://leoimpett.github.io/2dclip/](https://leoimpett.github.io/2dclip/)

DV Explorer  
Impett, L. (n.d.). DV Explorer. Retrieved from [https://distantviewing.org/tools/](https://distantviewing.org/tools/)

<!-- This assignment is ready to be graded. -->