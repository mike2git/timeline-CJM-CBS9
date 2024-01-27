# timeline-CJM-CBS9
Timeline CJM and CBS9

```mermaid
gantt
    tickInterval month
    axisFormat %B %Y
    dateFormat YYYY-MM-DD
    excludes 2024-07-01,2024-07-02,2024-07-03,2024-07-04,2024-07-05,2024-07-06,2024-07-07,2024-07-08,2024-07-09,2024-07-10,2024-07-11,2024-07-12,2024-07-13,2024-07-14,2024-07-15,2024-07-16,2024-07-17,2024-07-18,2024-07-19,2024-07-20,2024-07-21,2024-07-22,2024-07-23,2024-07-24,2024-07-25,2024-07-26,2024-07-27,2024-07-28,2024-07-29,2024-07-30,2024-07-31,2024-08-01,2024-08-02,2024-08-03,2024-08-04,2024-08-05,2024-08-06,2024-08-07,2024-08-08,2024-08-09,2024-08-10,2024-08-11,2024-08-12,2024-08-13,2024-08-14,2024-08-15,2024-08-16,2024-08-17,2024-08-18,2024-08-19,2024-08-20,2024-08-21,2024-08-22,2024-08-23,2024-08-24,2024-08-25,2024-08-26,2024-08-27,2024-08-28,2024-08-29,2024-08-30,2024-08-31
    

    section WinIBW4
      Test et paramétrage WinIBW4 avec CBS8                    :W4,2023-11-01,2024-06-30
      Packaging, import scripts W3, test avec un étab.    :active, W4etp1,2023-11-01,2023-12-31
      (Re)packaging + reprise des scripts + test avec un étab. :active,testCJMdev,2024-01-01,2024-03-31
      Tests fonctionnels + doc. + soutien à la formation :active,testCJMdev,2024-04-01,2024-06-30
    section CJM env DEV
      Installation CJM env DEV                      :insCJMdev,2023-11-01,2024-01-31
      Test CJM env DEV                              :active,testCJMdev,2023-12-01,2024-01-31
    section CJM env TEST
      Inst. CJM env TEST                            :insCJMtest,2024-02-01,2024-02-29
      Test CJM env TEST                             :active,testCJMtest,2024-02-01,2024-02-29
      Jalon 1 => Validation TR par CJM              :crit,milestone,m1,after testCJMtest, 0d
    section CJM env PROD
      Inst. CJM env PROD                            :insCJMprod,2024-03-01,2024-03-31
      Test CJM env PROD                             :active,testCJMprod,2024-03-01,2024-03-31
      Jalon 2 => Utilisation de CJM - arrêt d'APCC  :crit,milestone,m2,after testCJMprod, 0d
      Interruption de service TR                    :crit,intTR,after m2, 3d
    section CBS8 -> CBS9 env DEV     
      Installation CBS9 (RHEL9+POSTGRESQL) env DEV  :insCBSdev,2024-04-01,2024-06-20
      Test WinIBW3&4/Sudoc avec CBS9 env DEV       :active,testCBSdev,2024-04-10,2024-06-20
      Test CJM avec CBS9 env DEV                    :active,testCBSCJMdev,2024-04-10,2024-06-20
      Test app. ABES                                :active,testCBSAPPdev,2024-05-20,2024-06-20
      Jalon 3 => GO-NOGO pour installation env TEST :crit,milestone,m3,after testCBSAPPdev, 0d
    section CBS8 -> CBS9 env TEST
      Installation CBS9 (RHEL9+POSTGRESQL) env TEST :insCBStest,2024-06-21,2024-09-25
      Test WinIBW3&4/Sudoc avec CBS9 env TEST                            :active,testCBStest,2024-06-30,2024-09-25
      Test CJM avec CBS9 env TEST                   :active,testCBSCJMtest,2024-06-30,2024-09-25
      Test app. ABES                                :active,testCBSAPPtest,2024-09-01,2024-09-25
      Jalon 4 => GO-NOGO pour installation env PROD :crit,milestone,m4,after testCBSAPPtest, 0d
    section CBS8 -> CBS9 env PROD
      Inst. CBS9 (R9+PG) PROD                       :insCBStest,2024-09-25,2024-10-30
      Test W3&4/S CBS9 PROD                       :active,testCBSprod,2024-09-30,2024-10-30
      Test CJM CBS9 PROD                            :active,testCBSCJMprod,2024-09-30,2024-10-30
      Test app. ABES                                :active,testCBSAPPprod,2024-09-30,2024-10-30
      Jalon 5 => GO-NOGO pour passer en PROD        :crit,milestone,m5,after testCBSAPPprod, 0d
      Interruption de service CBS/PSI               :crit,int,after m5, 3d
    section Support / Marge pour l'imprévu
      Support / Marge pour l'imprévu                :sup,2024-10-30,2024-12-31
```



[![](https://mermaid.ink/img/pako:eNqll99um0gUxl9lhNRto2AHBnAGS1spTrJpqnrjNd5aXflm1kxTVAwIBivdKO-yt93XyIvtDGM4_HPsqtz4BCbfj_nOmTPDo7aOfaaNtXsacb6KkLh4sP56G3GWbmmINnHEv6j79CHIfovTDeXo1QS9-qTu-pSz3d1P4hpMp4OrK_WIPazD3GcZwga2B8b5wDD1KsQQWhDaEDoQjiA8h5BA6FahaUAINBNoJtBMoJlAM4FmAs0Emgk0DDQMNAw0DDQMNAw0DDQMNAw0DDQLaFZJI2AqAVMJmErAVAKmEjCVgKkETCVgKgFTCZhKwFQCphIwlYCpBEwlYCoBUwmYSsBUAqYSMJWAqQRMJWAqAVMJmErAVAKmEjBVhKaq21WkfjO25kEcoWUQ3U6WtrqJ0IJlHDGOEprSzfN3ntJ7Vo5BdMvW6HLiEdRzjZfF61rCRUjbSLxCKT2j66_0PojudRRskjjlKFunQcIztLR0xCW4AOQREmD697BQpeI1t0xHS5vxxGwRRIirmSH0Zs5OkpKCTlHKkjTIGJLLtGSd9pJKjHx2-X7qs-1uArW5WDWStClDn-OoMDFioRT24_VQ_GRxzgMmpP9FIRVjZPuQTu9l2H1-lfkRIxGLtujq-mMJv40yTsOQtp-j3mscRBngmukxW1M6rFap9k6myEePensyi2tvUZ_NsPHkRa6ajcTuKDUgFrXfO51Dqu3pHJZ_T0MxHxP9-hZ9pGHgq2Qs5nLhFNimvCg-rm-CUOjGEdM3pk4_i00I1XnI8Pvdms3vrvrdkk-OcCtJY78q4r31fLRq263D8sotLN36kwdhkCm7fFYwB4im6fN_HPmvL2aXlz124aZdBbCyS5oiHqZ5UopmYnsP1kymo-_tC_Ug4ov5TlboI6ttvmxzg7fy120sif5VKEe9mb-7_uCezu68xc382vvjwwn8Y5GJibdn0WOjkQjVb61f7DMvF02l6rtua2028tAUr3a1jrh0fJ_g_ixPvFbLwnsBNEmG6GJy7SH0Az1k4l3MZgBw-gGqkCxZSDd3g9_vbu5QEucpCurJqFZ8p46seh1VxO7Ca-e-3a-Oyrt6BZX3WkMZwcbvin39BxJ_sDc2_Wwwq5NAh9mthz2cbj0cSfiJgqgRXFgwdYKqCPtwRRRdrVMRdqci9vTidkn0NGVVC6IQbk5e6qHdknCr851p1A5MqiSKalDiL4k2rau1ZLfKTFdc5v6Q8p7cH0n4idwfJqjcO53cJzQTW4BIU2Nendw7ndwfu7GI0Wcz73bfxlJuK053W_HypDj6nqEpTcXRunjf8LU4EKfP37d5CT4wrGNelic1f3ahOhpLSU3XNkycQwNffA0_yjsrjX9hG7bSxiIUZ1RhwUpbRU9iJM157H2L1tqYpznTtTyRn8FXAb0XnwTlzYRGf8Vx_U9t_Kg9aGPnfDgirokN5xxbI2Pk6No3bUzwkBDDsB08slzn3LWfdO2f4v_NoWmPMMG2ZdsjyxFrXGN-wON0qr7di0_4p_8BGF8Kdg?type=png)](https://mermaid.live/edit#pako:eNqll99um0gUxl9lhNRto2AHBnAGS1spTrJpqnrjNd5aXflm1kxTVAwIBivdKO-yt93XyIvtDGM4_HPsqtz4BCbfj_nOmTPDo7aOfaaNtXsacb6KkLh4sP56G3GWbmmINnHEv6j79CHIfovTDeXo1QS9-qTu-pSz3d1P4hpMp4OrK_WIPazD3GcZwga2B8b5wDD1KsQQWhDaEDoQjiA8h5BA6FahaUAINBNoJtBMoJlAM4FmAs0Emgk0DDQMNAw0DDQMNAw0DDQMNAw0DDQLaFZJI2AqAVMJmErAVAKmEjCVgKkETCVgKgFTCZhKwFQCphIwlYCpBEwlYCoBUwmYSsBUAqYSMJWAqQRMJWAqAVMJmErAVAKmEjBVhKaq21WkfjO25kEcoWUQ3U6WtrqJ0IJlHDGOEprSzfN3ntJ7Vo5BdMvW6HLiEdRzjZfF61rCRUjbSLxCKT2j66_0PojudRRskjjlKFunQcIztLR0xCW4AOQREmD697BQpeI1t0xHS5vxxGwRRIirmSH0Zs5OkpKCTlHKkjTIGJLLtGSd9pJKjHx2-X7qs-1uArW5WDWStClDn-OoMDFioRT24_VQ_GRxzgMmpP9FIRVjZPuQTu9l2H1-lfkRIxGLtujq-mMJv40yTsOQtp-j3mscRBngmukxW1M6rFap9k6myEePensyi2tvUZ_NsPHkRa6ajcTuKDUgFrXfO51Dqu3pHJZ_T0MxHxP9-hZ9pGHgq2Qs5nLhFNimvCg-rm-CUOjGEdM3pk4_i00I1XnI8Pvdms3vrvrdkk-OcCtJY78q4r31fLRq263D8sotLN36kwdhkCm7fFYwB4im6fN_HPmvL2aXlz124aZdBbCyS5oiHqZ5UopmYnsP1kymo-_tC_Ug4ov5TlboI6ttvmxzg7fy120sif5VKEe9mb-7_uCezu68xc382vvjwwn8Y5GJibdn0WOjkQjVb61f7DMvF02l6rtua2028tAUr3a1jrh0fJ_g_ixPvFbLwnsBNEmG6GJy7SH0Az1k4l3MZgBw-gGqkCxZSDd3g9_vbu5QEucpCurJqFZ8p46seh1VxO7Ca-e-3a-Oyrt6BZX3WkMZwcbvin39BxJ_sDc2_Wwwq5NAh9mthz2cbj0cSfiJgqgRXFgwdYKqCPtwRRRdrVMRdqci9vTidkn0NGVVC6IQbk5e6qHdknCr851p1A5MqiSKalDiL4k2rau1ZLfKTFdc5v6Q8p7cH0n4idwfJqjcO53cJzQTW4BIU2Nendw7ndwfu7GI0Wcz73bfxlJuK053W_HypDj6nqEpTcXRunjf8LU4EKfP37d5CT4wrGNelic1f3ahOhpLSU3XNkycQwNffA0_yjsrjX9hG7bSxiIUZ1RhwUpbRU9iJM157H2L1tqYpznTtTyRn8FXAb0XnwTlzYRGf8Vx_U9t_Kg9aGPnfDgirokN5xxbI2Pk6No3bUzwkBDDsB08slzn3LWfdO2f4v_NoWmPMMG2ZdsjyxFrXGN-wON0qr7di0_4p_8BGF8Kdg)
