---
layout: archive
title: "Bucket List"
permalink: /life/
author_profile: true
header:
  og_image: "research/ecdf.png"
---

Things I want to do before 
I am too old.Let me know if you have any recommendation or want to try it together. Also, Thanks to Sejal Dua for inspiring me to write this bucket list.

1. Raise a Medium-size Dog
2. Raise a Large-size Dog with My Babies Together
3. Run a half marathon
4. Dye for Bright Color Hair - Princess Pink
5. Dye for Bright Color Hair - Cool Blue
6. Try Balayage Hair Style
7. Observe Galaxies and Got Great Photos
8. Weekly Volunteer at Zoo or Nursing Home for at Least Month
9. Record a Family Moment using Hasselblad
10. When Move to a New City, Try at Least One local Photographer
11. Get Published inT Towards Data Science on Medium
12. Visit Thailand Again
13. Dine at a Michelin star restaurant
14. Visit Japan during March for Sakura Blossom
15. Try Japaneses Izakaya, Hot Spring and Nihon Teien during Winter
16. Vist Japan during Summer for Firework Festival
17. Go Vegan Weekly for At Least A Year
18. Study Aboard
19. Fall in Love
20. Visit Hawaii and Try Local Fruits Everyday
21. Join a Broadcast as A guest 
22. Get a Computer Sciences Degree (Less important) and Enjoy the Projects (more important)
23. Get a PhD Degree and Do Something be Proud of
24. Try a Local Markup Studio - Black-Owned Studio
25. Try a Local Markup Studio - White-Owned Studio
26. Try a Local Markup Studio - Vietnam or Thailand Artist
27. Get 3 Different Portrait from Street Artist
28. Bake during Sunday Morning
29. Visit Europe

<nbsp>

{% include base_path %}

{% assign ordered_pages = site.research | sort:"order_number" %}

{% for post in ordered_pages %}
  {% include archive-single.html type="grid" %}
{% endfor %}
