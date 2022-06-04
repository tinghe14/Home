---
layout: archive
title: "Bucket List"
permalink: /life/
author_profile: true
header:
  og_image: "research/ecdf.png"
---

Things I want to do before I am too old. Let me know if you have any recommendations or want to try it together. Also, Thanks to Sejal Dua for inspiring me to write this bucket list.

1. ✅ [Raise a Medium-size Dog](https://drive.google.com/file/d/15dVCROMNh7xRlooGsmxJ_JF4DGwrfMcU/view?usp=sharing)
2. Raise a Large-size Dog and Grow up with My Human Babies Together
3. Run a half marathon
4. Dye for Bright Color Hair - Princess Pink
5. ✅ [Dye for Bright Color Hair - Cool Blue](https://drive.google.com/file/d/1wgUR36UG_Bi3rJCcvexH9GULRH-cuN0d/view?usp=sharing)
6. Try Balayage Hair Style
7. Observe Galaxies and Got Great Photos
8. Weekly Volunteer at Zoo or Nursing Home for at Least Month
9. Record Family Moment using Hasselblad
10. When Move to a New City, Try at Least One local Photographer
11. Get Published in Towards Data Science on Medium
12. Visit Thailand Again
13. Dine at a Michelin star restaurant
14. Visit Japan during March for Sakura Blossom
15. Try Japanese Izakaya, Hot Spring, and Nihon Teien during Winter
16. Visit Japan during Summer for Firework Festival
17. Go Vegan Once A Week for at Least A Year
18. ✅ Study Aboard
19. Fall in Love and Maintain Healthy Relationships
20. Visit Hawaii and Try Local Fruits Everyday
21. Join a Broadcast as A guest 
22. Get a Computer Sciences Degree (Less important) and Enjoy the Projects (more important)
23. Get a Ph.D. Degree and Do Something Being Proud of
24. Try a Local Markup Studio - Black Artist
25. Try a Local Markup Studio - White Artist
26. Try a Local Markup Studio - Vietnam or Thailand Artist
27. Get 3 Different Portraits from Street Artist
28. Bake When wake up at Sunday Morning
29. Visit Europe
30. Try  Local Jazz Pub
31. ✅ Experience Turbo Drop once 
32. ✅ Group Travel with Best Friends
33. Work at Silicon Valley
34. ✅ Experience New York Life
35. Visit Nepal or Tibet
36. Attend Lights Festival
37. Try EDC (Such as Tomorrowland in Belgium)
38. Scuba Diving 
39. Enjoy Exercise and Keep Fit
40. Visit Golden Bridge and Drive at No.1 Highway
41. Have Two Babies (If lucky, Big Brother with Little Sister is My Dream Combination)
42. Attend a Concert of Classical Music
43. Get a Tesla
44. Own One Bag Per Luxury Brand
45. ✅ See the Sunrise at Eastern Coast of the US (https://drive.google.com/file/d/1SI1DK9TwXzLcFaHi23eDpdtWgZke_azD/view?usp=sharing)
46. Check the Sunset at Western Coast of the US
47. Attend El Día de los Muertos at Mexico 
48. ✅ Attend Halloween Parade at New York(https://drive.google.com/file/d/11ZBQfJXNHB1FIhw737f3oSXlXOzxzkyF/view?usp=sharing)
49. Attend Time Square Ball Drop Event at New York
50. Visit Banff National Park and Visit My Mentor at Alberta, Canada
51. Have Fun in Taiwan
52. ✅ Have a Home Graden(https://drive.google.com/file/d/1dldtf_5UOZ7O066KcvL1gR_KedUpW43e/view?usp=sharing) 
53. Sleepover and Watch Honor Movie with Bunch of Friends
54. Try Different Sports Every Year
55. ✅ Log Cabin Forest Getaway
56. ✅ Enjoy a Night at a Comfortable RV(https://drive.google.com/file/d/1u3wD9tIcmARL8g0RTAvLB4rXHT0UEirf/view?usp=sharing)
57. Enjoy a Night at Sailboat
58. Spend Some Days at Farm
59. Jogging Everyday
60. Enjoy July 4th Firework at DC
61. ✅ Be Able to Ski at Green Line(https://drive.google.com/file/d/1ek0RYJ8ONctuN6f3ka90WS5d8A7vnNoL/view?usp=sharing)

<nbsp>

{% include base_path %}

{% assign ordered_pages = site.research | sort:"order_number" %}

{% for post in ordered_pages %}
  {% include archive-single.html type="grid" %}
{% endfor %}
