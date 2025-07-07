
# 📝 Dynamic Pricing for Urban Parking Lots – Model Summary

**Capstone Project – Summer Analytics 2025**  
Hosted by Consulting & Analytics Club × Pathway

---

## ✅ Objective

Design a dynamic pricing engine for 14 urban parking lots based on real-time data.  
This report summarizes the logic behind the 3 models implemented in the project notebook.

---

## 📊 Model 1: Baseline Linear Pricing

**Logic:**  
Price increases linearly with occupancy.

**Formula:**  
```
Priceₜ₊₁ = Priceₜ + α × (Occupancy / Capacity)
```

**Use Case:**  
Acts as a simple reference model to observe the effect of occupancy on pricing.

---

## 📈 Model 2: Demand-Based Pricing

**Logic:**  
Pricing is influenced by a linear combination of:
- Occupancy Rate
- Queue Length
- Traffic Level
- Special Events
- Type of Incoming Vehicle

**Formula:**  
```
Demand = α·(Occ/Cap) + β·Queue − γ·Traffic + δ·SpecialDay + ε·VehicleType
Price = Base × (1 + λ × NormalizedDemand)
```

**Assumptions:**
- Vehicle types like truck > car > bike influence price.
- Events or holidays increase demand.
- High traffic near the lot reduces appeal, slightly lowering price.

---

## 🧠 Model 3: Competitive Pricing (Optional)

**Logic:**  
Adjust price based on nearby competitor pricing and geographic proximity.

**Key Factors:**
- Uses Haversine distance to check if lots are within 1 km.
- If own lot is full and competitors are cheaper → lower price or reroute.
- If nearby lots are expensive → increase price while staying competitive.

**Assumptions:**
- Real-world users compare parking lots based on price & distance.
- Encourages balancing occupancy between close lots.

---

## 🧪 Common Features Used

| Feature             | Use in Models            |
|---------------------|--------------------------|
| Occupancy           | All Models               |
| Capacity            | Normalization            |
| Queue Length        | Model 2 & 3              |
| Traffic Level       | Model 2                  |
| Vehicle Type        | Model 2                  |
| Special Day Flag    | Model 2                  |
| Nearby Prices       | Model 3                  |

---

## 📌 Notes

- Prices are clipped to be between 0.5x and 2.0x base price to avoid volatility.
- Final pricing engine ensures **smooth, explainable, and bounded** changes.

---

**Author:** SUMIT JAISWAL  
**Notebook:** Dynamic_Pricing_Urban_Parking_Capstone.ipynb  
