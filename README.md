# Personal-Projects
🧪 Experimental playground where passion projects come to life. Learning by building, one curiosity at a time.

# 🌸 Perfume Recommendation System
An intelligent perfume recommendation system combining olfactory science with algorithmic precision. Born from a personal passion for fragrance and the art of scent composition.
---

## 🎯 Overview

This project implements a sophisticated perfume recommendation system that goes beyond simple preference matching. It evaluates **olfactory harmony** between notes and uses **fuzzy semantic matching** to identify user archetypes, generating personalized fragrance compositions that are both mathematically optimized and artistically balanced.

While developed as part of an academic course, this system reflects years of personal fascination with perfumery, from understanding the three-tier pyramid structure (top, middle, base notes) to appreciating how certain scent families interact synergistically.

---

## ✨ Key Features

### 🎼 **Harmony Scoring System**
- **Compatibility Matrix**: Quantifies how well different olfactory families blend together
- **Inter-layer Evaluation**: Assesses harmony across Top → Middle → Base notes
- **Weighted Scoring**: Balances individual note preferences with overall composition coherence

### 🔍 **Fuzzy Archetype Identification**
- **Semantic Matching**: Identifies the closest user archetype even when preferences don't perfectly align
- **Dynamic Adaptation**: Works with new user profiles without requiring exact matches to predefined types
- **Weighted Similarity**: Considers overlaps in families, characteristics, and dislikes

### 📊 **Data-Driven Recommendations**
- **Olfactory Families**: Citrus, Floral, Woody, Oriental, Gourmand, and more
- **Pyramid Structure**: Proper separation of volatile (Top), heart (Middle), and base notes
- **Gender Fluidity**: Supports Masculine, Feminine, and Unisex preferences

---

## 🔬 Technical Deep Dive

### **Algorithm Flow**

#### 1️⃣ **Data Structures**
```python
# Olfactory Notes Database
olfactory_df = pd.DataFrame({
    'Note': ['Bergamot', 'Rose', 'Sandalwood', ...],
    'Family': ['Citrus', 'Floral', 'Woody', ...],
    'Pyramid_Layer': ['Top', 'Middle', 'Base', ...],
    'Characteristics': ['Fresh', 'Romantic', 'Creamy', ...],
    'Gender_Target': ['Unisex', 'Feminine', 'Masculine', ...]
})
```

#### 2️⃣ **Scoring Mechanism**
- **Family Match**: +3 points
- **Characteristic Match**: +2 points  
- **Gender Match**: +1 point
- **Disliked Note**: -10 points (hard exclusion)
- **Gender Mismatch**: -0.5 points (soft penalty)

#### 3️⃣ **Harmony Evaluation**
```python
def calculate_harmony_score(composition, compatibility_matrix_df):
    """
    Evaluates inter-family compatibility across all note pairs
    Returns: Average compatibility score (0.0 - 1.0)
    """
    harmony_scores = []
    for note1, note2 in itertools.combinations(all_notes, 2):
        score = get_compatibility(family1, family2)
        harmony_scores.append(score)
    
    return np.mean(harmony_scores)
```

#### 4️⃣ **Fuzzy Archetype Matching**
```python
def calculate_fuzzy_similarity(user_prefs, archetype_profile):
    """
    Calculates weighted overlap between user preferences and archetype
    Components:
    - Family overlap (40% weight)
    - Characteristic overlap (40% weight)
    - Gender match (10% weight)
    - Dislike penalties (10% weight)
    """
    similarity_score = (
        0.4 * family_overlap +
        0.4 * characteristic_overlap +
        0.1 * gender_match -
        0.1 * dislike_penalty
    )
    return similarity_score
```

---

## 📈 Example Results

### **Modern Minimalist Archetype**
**Preferences**: Citrus, Green, Aquatic families | Fresh, Clean, Crisp characteristics

**Recommended Composition**:
- 🍋 **Top Notes**: Bergamot (Score: 6.0), Lemon (Score: 4.0)
- 🌿 **Middle Notes**: Geranium (Score: 1.0)
- 🌫️ **Base Notes**: Musk (Score: 3.0), Patchouli (Score: 1.0)

**Metrics**:
- Harmony Score: `0.533`
- Final Total Score: `15.33`

---

### **Adventurous Explorer Archetype**  
**Preferences**: Woody, Spicy, Chypre families | Earthy, Dry, Smoky characteristics

**Recommended Composition**:
- 🌶️ **Top Notes**: Pink Pepper (Score: 4.0)
- 🌸 **Middle Notes**: Geranium (Score: 1.0)
- 🌲 **Base Notes**: Vetiver (Score: 6.0)

**Metrics**:
- Harmony Score: `0.567`
- Final Total Score: `16.67`
- Archetype Similarity: `0.67` (identified via fuzzy matching)

---

## 🚀 Getting Started

### **Prerequisites**
```bash
Python 3.8+
pandas
numpy
```

### **Installation**
```bash
# Clone the repository
git clone https://github.com/yourusername/perfume-recommendation-system.git
cd perfume-recommendation-system

# Install dependencies
pip install pandas numpy

# Open the notebook
jupyter notebook perfume_recommendation_v2.ipynb
```

### **Quick Usage**
```python
# Define your preferences
my_preferences = {
    'Preferred_Families': ['Floral', 'Fruity', 'Gourmand'],
    'Preferred_Characteristics': ['Sweet', 'Romantic', 'Warm'],
    'Disliked_Notes': ['Oud', 'Vetiver', 'Incense'],
    'Gender_Target_Preference': 'Feminine'
}

# Get recommendation
recommendation = recommend_perfume_for_new_user(
    my_preferences, 
    archetype_df, 
    olfactory_df, 
    compatibility_matrix_df
)

print(recommendation)
```

---

## 📊 Predefined Archetypes

| Archetype | Families | Characteristics | Target |
|-----------|----------|-----------------|--------|
| **Modern Minimalist** | Citrus, Green, Aquatic | Fresh, Clean, Crisp | Unisex |
| **Classic Romantic** | Floral, Chypre, Oriental | Romantic, Powdery, Sweet | Feminine |
| **Adventurous Explorer** | Woody, Spicy, Leather | Earthy, Smoky, Resinous | Masculine |
| **Gourmand Lover** | Gourmand, Oriental, Fruity | Sweet, Warm, Creamy | Feminine |
| **Elegant Professional** | Chypre, Woody, Musky | Sophisticated, Subtle, Refined | Unisex |

---

## 🎨 The Personal Side

### Why Perfume?

Fragrance is one of the most intimate forms of self-expression. Unlike visual aesthetics, scent is invisible yet unforgettable—it can evoke memories, signal presence, and communicate personality without words. 

This project emerged from:
- **Years of collecting and analyzing fragrances** (from niche houses to commercial giants)
- **Fascination with the chemistry** of how volatile compounds evolve over time on skin
- **Curiosity about the art** of perfumery: Why does Bergamot + Vetiver work? Why is Rose + Oud iconic?

The goal wasn't just to build a recommendation system—it was to **codify intuition**. Can an algorithm capture the magic that a master perfumer ("the nose") creates through decades of experience?

This project is my attempt to bridge that gap: respecting the art while leveraging the precision of computation.

---

## 🔮 Future Enhancements

### **Short-term Roadmap**
- [ ] Expand olfactory database to 200+ notes
- [ ] Implement threshold-based note filtering
- [ ] Add visualization of composition pyramids
- [ ] Create web interface for interactive recommendations

### **Long-term Vision**
- [ ] **Machine Learning Integration**: Train on real perfume ratings from Fragrantica/Basenotes
- [ ] **Seasonal Recommendations**: Adjust for weather/temperature
- [ ] **Concentration Translator**: Convert scores to actual % formulations
- [ ] **IFRA Compliance Checker**: Validate against regulatory restrictions
- [ ] **User Feedback Loop**: Adaptive learning from user ratings

---

## 🤝 Contributing

This project is open to contributions! Whether you're a perfume enthusiast, data scientist, or both, feel free to:

- **Report issues** with recommendations
- **Suggest new archetypes** or olfactory families
- **Improve the harmony matrix** with domain knowledge
- **Add features** from the roadmap

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## 📚 References & Inspiration

### **Books**
- *The Perfect Scent* by Chandler Burr
- *Perfumes: The Guide* by Luca Turin & Tania Sanchez

### **Technical Resources**
- [Fragrantica](https://www.fragrantica.com/) - Perfume database
- [IFRA Standards](https://ifrafragrance.org/) - Regulatory guidelines
- Olfactory pyramid theory (Piesse, 1857)

### **Datasets**
- Olfactory note classifications based on traditional perfumery families
- Compatibility matrix inspired by classic fragrance combinations

---

## 👤 Author

**Developed by someone passionate about perfumery**

*Combining a love for fragrance with computational thinking to bridge the gap between art and algorithm.*

<p align="center">
  <i>Built with 💙 for the art of scent and the science of recommendation systems</i>
</p>

<p align="center">
  <sub>⭐ If you found this project interesting, consider giving it a star!</sub>
</p>

