# timeline-CJM-CBS9
Timeline CJM and CBS9

```mermaid
gantt
    tickInterval month
    axisFormat %B %Y
    dateFormat YYYY-MM-DD
    excludes 2024-07-01,2024-07-02,2024-07-03,2024-07-04,2024-07-05,2024-07-06,2024-07-07,2024-07-08,2024-07-09,2024-07-10,2024-07-11,2024-07-12,2024-07-13,2024-07-14,2024-07-15,2024-07-16,2024-07-17,2024-07-18,2024-07-19,2024-07-20,2024-07-21,2024-07-22,2024-07-23,2024-07-24,2024-07-25,2024-07-26,2024-07-27,2024-07-28,2024-07-29,2024-07-30,2024-07-31,2024-08-01,2024-08-02,2024-08-03,2024-08-04,2024-08-05,2024-08-06,2024-08-07,2024-08-08,2024-08-09,2024-08-10,2024-08-11,2024-08-12,2024-08-13,2024-08-14,2024-08-15,2024-08-16,2024-08-17,2024-08-18,2024-08-19,2024-08-20,2024-08-21,2024-08-22,2024-08-23,2024-08-24,2024-08-25,2024-08-26,2024-08-27,2024-08-28,2024-08-29,2024-08-30,2024-08-31
    

    section CJM sur CBS8 env DEV
      Installation CJM env DEV         :insCJMdev,2023-11-01,2024-01-31
      Test CJM env DEV  :active,testCJMdev,2023-12-01,2024-01-31
    section CJM sur CBS8 env TEST
      Inst. CJM env TEST         :insCJMtest,2024-02-01,2024-02-29
      Test CJM env TEST         :active,testCJMtest,2024-02-01,2024-02-29
      Jalon 1 => Validation TR par CJM       :crit,milestone,m1,after testCJMtest, 0d
    section CJM sur CBS8 env PROD
      Inst. CJM env PROD         :insCJMprod,2024-03-01,2024-03-31
      Test CJM env PROD  :active,testCJMprod,2024-03-01,2024-03-31
      Jalon 2 => Utilisation de CJM - arrêt d'APCC       :crit,milestone,m2,after testCJMprod, 0d
      Interruption de service TR :crit,intTR,after m2, 3d
    section CBS8 -> CBS9 env DEV     
      Installation CBS9 (RHEL9+POSTGRESQL) env DEV   :insCBSdev,2024-04-01,2024-06-20
      Test CBS9 env DEV   :active,testCBSdev,2024-04-10,2024-06-20
      Test CJM avec CBS9 env DEV   :active,testCBSCJMdev,2024-04-20,2024-06-20
      Test app. ABES  :active,testCBSAPPdev,2024-05-20,2024-06-20
      Jalon 3 => GO-NOGO pour installation env TEST       :crit,milestone,m3,after testCBSAPPdev, 0d
    section CBS8 -> CBS9 env TEST
      Installation CBS9 (RHEL9+POSTGRESQL) env TEST   :insCBStest,2024-06-21,2024-09-25
      Test CBS9 env TEST   :active,testCBStest,2024-06-30,2024-09-25
      Test CJM avec CBS9 env TEST   :active,testCBSCJMtest,2024-06-30,2024-09-25
      Test app. ABES  :active,testCBSAPPtest,2024-09-01,2024-09-25
      Jalon 4 => GO-NOGO pour installation env PROD       :crit,milestone,m4,after testCBSAPPtest, 0d
    section CBS8 -> CBS9 env PROD
      Inst. CBS9 (R9+PG) PROD   :insCBStest,2024-09-25,2024-10-30
      Test CBS9 env PROD   :active,testCBSprod,2024-09-30,2024-10-30
      Test CJM CBS9 PROD   :active,testCBSCJMprod,2024-09-30,2024-10-30
      Test app. ABES  :active,testCBSAPPprod,2024-09-30,2024-10-30
      Jalon 5 => GO-NOGO pour passer en PROD       :crit,milestone,m5,after testCBSAPPprod, 0d
      Interruption de service CBS/PSI :crit,int,after m5, 3d
    section Support / Marge pour l'imprévu
      Support / Marge pour l'imprévu   :sup,2024-10-30,2024-12-31
```
