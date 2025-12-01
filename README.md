# Urban-Climate-Analytics-NYC

This repository contains a machine learning project that predicts Urban Heat Island (UHI) intensity using satellite imagery and environmental indices. The analysis combines Sentinel-2 multi-spectral GeoTIFF data with ground-truth UHI measurements to generate high-resolution spatial heat maps for New York City.

The project demonstrates skills in geospatial data processing, remote sensing feature engineering, supervised machine learning, and spatial prediction visualization.



## 1. Project Overview

Urban Heat Islands occur when built environments retain more heat than surrounding areas, disproportionately affecting dense and low-vegetation neighborhoods.  
This project builds a predictive model capable of estimating UHI intensity at the pixel level using satellite imagery.

### **Objective**
Build a machine learning model using Python and Sentinel-2 satellite data to predict UHI intensity across New York City.

### **Key Approach**
- Processed multi-spectral Sentinel-2 GeoTIFF imagery
- Computed NDVI (Normalized Difference Vegetation Index) and NDWI (Normalized Difference Water Index)
- Merged **11,229** ground-truth UHI measurements with pixel-aligned satellite data
- Trained a Random Forest Regression model to estimate UHI intensity
- Generated heat maps for Manhattan and the Bronx based on model predictions



## 2. Dataset

### **Satellite Data (Sentinel-2)**
- Multi-spectral GeoTIFF scenes  
- Bands used to compute NDVI, NDWI, and other environmental indicators  
- Spatial resolution: 10m / 20m  
- Covers Manhattan and Bronx regions

### **Ground-Truth UHI Measurements**
- 11,229 recorded UHI index values
- Mapped to pixel-level satellite grid
- Used as regression target for model training

### **Derived Features**
- **NDVI** (vegetation density)
- **NDWI** (surface moisture)
- **Surface reflectance** from Sentinel-2 bands
- **Pixel-level spectral signatures** describing heat-retaining materials



## 3. Methods

### **1. Data Preprocessing**
- Read and stacked GeoTIFF multi-band arrays  
- Reprojected imagery to consistent CRS  
- Cropped large tiles to selected NYC regions  
- Computed NDVI and NDWI vegetation indices  
- Merged satellite features with UHI labels

### **2. Feature Engineering**
- Added spectral ratio features
- Added vegetation & moisture indices (NDVI/NDWI)
- Normalized continuous spectral metrics
- Removed invalid or cloudy pixels

### **3. Modeling**
**Model:** Random Forest Regressor  
**Training/Test Split:** 80/20  
**Evaluation Metrics:**
- **Test R²:** 0.393  
- **Test RMSE:** 0.0127  

> Interpretation:  
> - R² indicates the model captures meaningful spatial variation in UHI intensity  
> - RMSE is small due to the compact numerical range of the UHI index  
> - Predictions are smooth and consistent across space, suitable for heat-map inference

### **4. Prediction Output**
- Pixel-level UHI prediction for selected regions
- Generated high-resolution heat maps:
  - Predicted Urban Heat Island Intensity  
  - NDWI vegetation distribution  


## 4. Visual Outputs

<img width="701" height="405" alt="Screenshot 2025-11-30 at 10 39 01 PM" src="https://github.com/user-attachments/assets/85a4f955-e84e-4cf6-9478-89169f7cd114" />

## 5. Key Findings

- Areas with low NDVI (low vegetation cover) show the highest predicted UHI intensity
- Water-adjacent and high-moisture areas exhibit lower UHI (supported by NDWI distribution)
- Dense urban cores such as Midtown Manhattan show strong thermal retention signatures
- The Random Forest model effectively identifies spatial patterns driven by vegetation and surface features
- Mapping outputs align with known UHI hotspots documented in environmental research

## 7. Tools & Libraries

- numpy
- pandas
- rasterio
- matplotlib
- scikit-learn
- geopandas (if used)
- seaborn
- Techniques
- Remote sensing analysis
- Vegetation index computation (NDVI/NDWI)
- Random Forest regression
- Spatial prediction
- Geospatial raster handling

## 8. Conclusion

This project demonstrates the use of machine learning and satellite imagery to model urban heat intensity at a fine spatial scale. The workflow highlights:

- How environmental indices derived from remote sensing can explain UHI variation
- How geospatial machine learning can inform urban planning and climate adaptation
- The potential for scalable, pixel-level UHI prediction across major cities
- Future extensions may include:
- Integrating land-use classification
- Using LightGBM or CNN-based spatial models
- Expanding prediction to additional boroughs or U.S. cities
