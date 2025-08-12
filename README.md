# Conceptual Case Study: ML Engineering, Workflow Automation, and Cost Optimization on Databricks

> **Disclaimer**  
> This is a fictional scenario inspired by public machine learning engineering practices.  
> No proprietary data, processes, or results from any specific employer are included.

---

## Problem
A fictional **ML engineering team** needed to build a scalable environment for **developing, training, and deploying machine learning models** on large Delta datasets while:
- Maintaining reproducibility and collaboration.
- Controlling cloud compute costs.
- Automating end-to-end workflows for repeatable production runs.

---

## Approach
1. **Data Management**
   - Structured data in **Delta tables** stored in managed volumes.
   - Applied partitioning and ordering strategies (fictional) to improve read performance.

2. **Model Development**
   - Used notebooks for feature engineering, model training, and evaluation.
   - Tracked experiments in **MLflow** with:
     - Parameters
     - Metrics
     - Model artifacts
   - Promoted successful models through **Model Registry** for versioned deployment.

3. **Workflow Automation**
   - Created **multi-task Jobs** representing the model pipeline:
     ```
     data_prep → feature_build → train → validate → register_model →
     ```
   - Defined task dependencies, retry policies, and parameterized runs.
   - Configured **ephemeral job clusters** for each task to reduce idle compute usage.
   - Automated notifications for run completions or failures.

4. **Compute Cost Optimization**
   - Selected **cluster sizes and node types** based on workload profiles.
   - Set short **auto-termination windows** to avoid paying for idle clusters.
   - Batched non-urgent experiments to reduce repeated spin-ups.
   - Logged **estimated run costs** alongside metrics in Databricks system tables for review.

5. **Pandas vs Spark Tuning**
   - Used Pandas for small, targeted data slices to minimize overhead.
   - Used Spark for large joins, aggregations, or distributed feature computation.
   - Minimized `collect()` and leveraged Arrow for Pandas ↔ Spark transfers.
   - Applied broadcast joins, repartitioning, and skew-handling strategies for performance.



## Challenges
- Determining when to use Pandas vs Spark in model pipelines to balance cost and performance.
- Coordinating multiple workflows without exceeding cluster resource limits.

## Outcome (Fictional)
- Reduced monthly compute spend through **cluster right-sizing, auto-termination, and caching**.
- Increased iteration speed with **parameterized workflows** and precomputed features.
- Improved model lifecycle management through **MLflow tracking and registry workflows**.


## Visual
**Caption:** Mock Databricks job DAG and fictional compute cost trend showing post-optimization improvements.  
![Databricks](/db_plot.png)

## Key Skills

### ML Engineering
- Feature engineering on **Delta**
- Reproducible training and deployment with **MLflow** + **Model Registry**

### Workflow Automation
- **Databricks Jobs**: DAG creation, parameterization, retry logic, notifications
- Ephemeral cluster strategy for task isolation

### Cost & Performance Optimization
- Cluster sizing, auto-termination, off-peak scheduling
- Pandas vs Spark decision rules for cost-effective pipeline execution
- Caching and data pruning in Delta

### Tools & Platform
- **Databricks** (Delta tables, Volumes, Notebooks, Jobs, Model Registry)
- **MLflow**
- PySpark, Pandas
