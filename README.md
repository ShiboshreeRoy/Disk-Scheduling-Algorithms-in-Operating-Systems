# **Disk Scheduling Algorithms in Operating Systems**  

## **Overview**  
Disk scheduling plays a crucial role in optimizing seek time and improving overall system performance. This document provides a detailed explanation of six commonly used disk scheduling algorithms, along with examples and comparative analysis.  

## **Algorithms Covered**  
- **First Come First Serve (FCFS)**  
- **Shortest Seek Time First (SSTF)**  
- **SCAN (Elevator Algorithm)**  
- **C-SCAN (Circular SCAN)**  
- **LOOK**  
- **C-LOOK (Circular LOOK)**  

---

## **1. First Come First Serve (FCFS)**  
### **Description**  
- The simplest scheduling algorithm.  
- Processes disk requests in the order they arrive.  
- Can lead to high seek times due to long jumps.  

### **Example**  
**Request Queue:** `98, 183, 37, 122, 14, 124, 65, 67`  
**Initial Head Position:** `53`  

#### **Processing Order:**  
```
53 → 98 → 183 → 37 → 122 → 14 → 124 → 65 → 67
```
**Total Seek Time:** `640 cylinders`  

### **Pros & Cons**  
✅ Simple and fair.  
❌ High seek time, inefficient for large workloads.  

---

## **2. Shortest Seek Time First (SSTF)**  
### **Description**  
- Selects the request closest to the current head position.  
- Reduces seek time but can cause starvation for distant requests.  

### **Example**  
**Processing Order:**  
```
53 → 65 → 67 → 37 → 14 → 98 → 122 → 124 → 183
```
**Total Seek Time:** `236 cylinders`  

### **Pros & Cons**  
✅ Faster than FCFS.  
❌ Starvation risk for distant requests.  

---

## **3. SCAN (Elevator Algorithm)**  
### **Description**  
- Moves in one direction, servicing all requests, then reverses.  
- Prevents starvation compared to SSTF.  

### **Example**  
**Processing Order:**  
```
53 → 65 → 67 → 98 → 122 → 124 → 183 → 199 → 14 → 37
```
**Total Seek Time:** `354 cylinders`  

### **Pros & Cons**  
✅ Prevents starvation.  
❌ Can have long wait times for extreme requests.  

---

## **4. C-SCAN (Circular SCAN)**  
### **Description**  
- Like SCAN but jumps to the lowest request after reaching the highest.  
- Ensures uniform wait time for all requests.  

### **Example**  
**Processing Order:**  
```
53 → 65 → 67 → 98 → 122 → 124 → 183 → 199 → 0 → 14 → 37
```
**Total Seek Time:** `382 cylinders`  

### **Pros & Cons**  
✅ Provides uniform wait times.  
❌ Higher seek time than SCAN.  

---

## **5. LOOK**  
### **Description**  
- Similar to SCAN but stops at the last request before reversing.  
- Reduces unnecessary head movements.  

### **Example**  
**Processing Order:**  
```
53 → 65 → 67 → 98 → 122 → 124 → 183 → 37 → 14
```
**Total Seek Time:** `299 cylinders`  

### **Pros & Cons**  
✅ Faster than SCAN.  
❌ More complex than FCFS and SSTF.  

---

## **6. C-LOOK (Circular LOOK)**  
### **Description**  
- Like C-SCAN but stops at the last request and jumps back to the smallest request.  
- More efficient than C-SCAN.  

### **Example**  
**Processing Order:**  
```
53 → 65 → 67 → 98 → 122 → 124 → 183 → 14 → 37
```
**Total Seek Time:** `322 cylinders`  

### **Pros & Cons**  
✅ Faster than C-SCAN.  
❌ More complex than LOOK.  

---

## **Comparison Table**  

| Algorithm | Seek Time | Starvation Risk | Direction Reversal? |
|-----------|-----------|-----------------|------------------|
| **FCFS**  | High      | No              | No              |
| **SSTF**  | Medium    | Yes             | No              |
| **SCAN**  | Medium    | No              | Yes             |
| **C-SCAN**| Medium    | No              | No (jumps)      |
| **LOOK**  | Low       | No              | Yes             |
| **C-LOOK**| Lowest    | No              | No (jumps)      |

---

## **Conclusion**  
- **FCFS** is simple but inefficient.  
- **SSTF** is faster but can cause starvation.  
- **SCAN & LOOK** prevent starvation with moderate seek time.  
- **C-SCAN & C-LOOK** provide the best performance for high workloads.  

For optimal performance, **LOOK and C-LOOK** are generally preferred due to reduced seek time and better efficiency.  

---

### **Author:**  
Shiboshree Roy 

### **License:**  
This project is open-source and available under the MIT License.
