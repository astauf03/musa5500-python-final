# 📝 Remaining To-Do List for Accessibility Project

## 🔧 1. Fix HTML Interactive Map
- Move `interactive_accessibility_map.html` into `docs/interactive/`
- Update iframe path in `results.md` to:
<iframe src="../interactive/interactive_accessibility_map.html" ...> ``` - Verify it loads when running `mkdocs serve`
---
## 🖼️ 2. Ensure All Maps & Figures Are Exported Correctly

Export the following PNGs into docs/assets/:

accessibility_score_map.png

accessibility_components.png

psq_radar.png

top5_parallel_coordinates.png

amenity_components.png

amenity_score_map.png

amenity_components_hist.png

mobility_component_maps.png

environmental_components.png

environmental_score_map.png

social_components.png

psq_city_histograms.png

psq_social_rank.png

Then update paths in markdown like:

![Title](../assets/filename.png)


We might need more... i have some placeholder png's in there that do not work yet because they do not exist, ESP in the **mobility.ipynb**


## 3. Update methodology.md
This file is nearly empty — needs full content:
Add:


NDVI calculation & normalization


Park, health, and service proximity (KDTree method)


Sidewalk gap detection (NetworkX components)


Cartway density method


Bike lane density method


ACS processing + demographic inversions


Min-max normalization formula


Weighted accessibility score formula


Neighborhood aggregation (tract → hood)



## 4. Fill in Missing Interpretation Sections
The following pages still contain placeholders:


environmental_score.md → Interpretation paragraph


land_use_score.md → Expand key findings


mobility_score.md → Add histogram + interpretation


social_score.md → Add narrative under components & citywide patterns


accessibility_score.md → Expand interpretation of domain comparison grid



## 5. Write the Conclusion


Summarize how PSQ performs across all domains


Identify citywide trends


Provide planning implications


Explain limitations & future improvements



## 6. Re-run Final Notebook to Confirm Scores
In allmaps.ipynb, verify:


Correct weighting:
0.4 * mobility + 0.3 * land use + 0.2 * env + 0.1 * social



No missing values in accessibility_score


Rankings align with plots (Top 5, radar chart, etc.)


Export final gdf if needed



## 7. Check All Links in Site Navigation
Run:
mkdocs serve

Then verify:


No broken images


No missing markdown pages


Navigation tabs work


MathJax equations render


##  8. Optional (If Time Allows)


Adjust equation color classes if needed (eq-blue, eq-gold, eq-red)


Clean figure titles & legends for consistency



✅ That’s the full remaining task list.

---

If you want, I can also create a **prioritized list**, a **checklist with estimated time**, or a version you can print.
