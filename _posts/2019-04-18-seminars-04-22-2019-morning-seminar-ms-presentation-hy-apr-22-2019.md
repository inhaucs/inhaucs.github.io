---
title: "Session 4. Signal Processing and Machine Learning with Differential Privacy"
date: 2019-04-18 00:00:00 Z
description: (blank)
card_title: Session 4
card_teaser: "Signal Processing and Machine Learning with Differential Privacy"
card_position: 4
icon: fa-server
categories: [seminars,04-22-2019-morning-seminar,presentation]
tags: [SPM, 2013, SPM2013, Signal Processing, Machine Learning, Differential Privacy]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-apr-22-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-04-22

## Information of the paper
+ Authors: Anand D. Sarwate (Toyota Technological Institute); Kamalika Chaudhuri (University of California)
+ Conference name: IEEE Signal Processing Magazine
+ Published date: 2013-08-19
+ [Paper file](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6582713)

## Abstract
Private companies, government entities, and institutions such as hospitals routinely gather vast amounts of digitized personal information about the individuals who are their customers, clients, or patients. Much of this information is private or sensitive, and a key technological challenge for the future is how to design systems and processing techniques for drawing inferences from this large-scale data while maintaining the privacy and security of the data and individual identities. Individuals are often willing to share data, especially for purposes such as public health, but they expect that their identity or the fact of their participation will not be disclosed. In recent years, there have been a number of privacy models and privacy-preserving data analysis algorithms to answer these challenges. In this article, we will describe the progress made on differentially private machine learning and signal processing.

## Summary (Korean)
+ 제목에 신호 처리와 기계 학습 차등정보 보호가 있으나, 전체적인 내용은 continuous data에 대한 차등정보 보호 방법들을 연구한 논문들을 Survey한 성향이 강한 논문.
+ *신호 처리*에 대해서는 continuous data에 대해서 설명할 때, 대표적으로 신호 처리가 있다라고 기술하는 정도임.

## Details
+ DP에서 완벽하게 안전한 알고리즘(Completely private algorithm)은 아무것도 주지 못함(release nothing).
+ DP 사용 시에 privacy guarantee epsilon, utility(유용성), 그리고 sample size n 사이에는 tradeoff 가 있음.
  + 이러한 tradeoff는 데이터들의 특성에 따라 다름(e.g., dimension, range, sparsity).
+ Motivation : Discrete data에 대한 DP 연구는 많은데, Continuous data에 대한 연구는 많이 진행되지 않음.
+ DP가 왜 중요하냐 : 그것은 다른 ML들이 취약한 공격에 강하기 때문 [GKS08]
+ DP 정의가 있긴한데 [[DMN+06]]를 보든가 해야지. 정확히 이해되지 않음. epsilon은 작을 수록 좋음.
+ epsilon-DP도 있고, (epsilon, delta)-DP도 있는데 epsilon과 delta 둘 다 작을 수록 프라이버시가 더 보장됨[[DMN+06]], [[WZ10]]. 또한 (epsilon, delta)-DP는 delta=0일 때, epsilon-DP로 reduction되고, epsilon-DP보다 더 약한 프라이버시를 보장함(그럼 왜 사용함?-설명 無).
+ (epsilon, delta)-DP의 여러 변형으로 (1, epsilon, delta)-indistinguishability [[CM06]]이나 delta-probabilistic privacy[[MKA+08]] 등이 있음.
+ DP의 중요한 특징 두 가지
  + epsilon-DP를 사용하여 출력된 결과를 사용하여 다른 작업을 수행하여도 epsilon-DP가 유지됨(Chain rule?)
  + 만약 같은 데이터에 대하여 epsilon1과 epsilon2에 대하여 프라이버시를 보장하는 알고리즘의 출력을 동시에 사용하는 경우 안전성은 epsilon1 + epsilon2가 됨.

## Generic Methods for Differential Privacy
+ Input perturbation : Input에 임의의 노이즈를 추가하여 학습하는 방법
+ Output perturbation : Output에 임의의 노이즈를 추가하여 출력하는 방법
+ Exponential mechanism : 이 부분은 정확히 모르겠으나 Mean Squared Error와 같은 최적화 알고리즘에 노이즈를 추가하여 계산하는 방법
+ Objective perturbation : 학습 시에 사용되는 Objective function에 노이즈를 추가하여 계산하는 방법
+ Exponential mechanism과 Objective perturbation의 차이?
+ 각 방법에 더해지는 노이즈는 특정 밀도를 따름.


## Signal processing and machine learning with privacy
+ [[CMS11]], [[RBH+12]], [[KST12]], [[C11]] : Classification
+ [[ZZX+12]], [[L11]] : Regression
+ [[CSS12]], [[HR13]], [[BDM+05]], [[KT13]] : Principal components analysis (PCA)
+ [[DRV10]] : Boosting
+ [[JKT12]] : Online learning
  + Logistic regression with continous value (논문 식 참조 필요, example임)
  + [[BDM+05]], [[CSS12]], [[MT07]] : PCA + DP
  + Time-series data + DP
    + [[RN10]] : Fourier + HE
    + [[FX12]] : Kalman filter + Laplace noise -> 이 논문은 discrete Fourier transform을 개량하는데 도움을 줌 [[RN10]].
    + [[LP12a]], [[LP12b]] : Signal processing + DP, Input pert. vs. Output pert. -> Input pert.가 더 성능이 좋음.

## Practical issues and limitations
+ 여기서도 가정이 너무 심함. e.g., Discrete data, finite hypothesis sets, bounded range[[CH11]], [[BKN10]].
+ epsilon과 delta의 초기 설정 문제 -> 이와 관련된 합의가 제안되긴 했음. [GKS08](초기 delta 설정 관련 논문)

## Future challenges
+ DP와 관련된 다른 논문들도 많은데 본 논문에서 소개하는 것은 너무 적음.
+ Challenge 1 : Signal을 수집하는 순간과 학습에 사용되기 전 어느 시점에서 Perturbation이 적용되어야 하는가에 대한 문제
+ Challenge 2 : 이미지와 같이 차원이 매우 높은 데이터에 대한 경우에 대한 연구 부족 (문제?)
+ Challenge 3 : 암호학적 접근과 관련된 연구들은 많으나, DP 관련 연구는 아직 초기임.(2013 논문이라 현재까지도 이게 Challenge가 될지는 모르겠음.)

## References
+ [[FWC+10]] : Survey paper of privacy-preserving machine learning (PPML)
+ [[DMN+06]] : Initial paper of differential privacy
+ [[RHM+09]], [[KM11]], [[CM06]] : Variants of differential privacy
+ [[DS09]] : Survey paper of differential privacy
+ [[LP12a]] [[LP12b]], [[FX12]] : Differential privacy for signal processing
+ [[CMS11]], [[RBH+12]] [[ZZX+12]] : Differential privacy for classification
+ [[CSS12]], [[HLM12]] : Differential privacy for dimensionality reduction
+ [[GR11]] : Differential privacy for auction design


## Point to note
+ Continuous data에 대한 privacy-preserving machine learning을 수행해야하는 경우 References 항목의 논문들 참조
+ 또한 Continous data에 대한 DP의 Overview를 위해 볼 수 있음

## Discussion
+ SUPER HAPPY

[FWC+10]: <https://www.cs.sfu.ca/~wangk/pub/FWCY10csur.pdf> "B. C. M. Fung, K. Wang, R. Chen, P. S. Yu, “Privacy-preserving data publishing: A survey of recent developments”, ACM Comput. Surv., vol. 42, no. 4, pp. 14:1-14:53, June 2010."
[DMN+06]: <http://people.csail.mit.edu/asmith/PS/sensitivity-tcc-final.pdf> " C. Dwork, F. McSherry, K. Nissim, and A. Smith. (2006, Mar. 4–7). Theory of Cryptography (Lecture Notes in Computer Science Series, vol. 3876) [Online]. Available: http://dx.doi.org/10.1007/11681878_14"
[GKS08]: <http://www.cse.psu.edu/~ads22/privacy598/papers/gks08.pdf> "S. R. Ganta, S. P. Kasiviswanathan, and A. Smith. Composition attacks and auxiliary information in data privacy. presented at the 14th ACM SIGKDD Int. Conf. Knowledge Discovery and Data Mining (KDD ’08) [Online]. Available: http://dx.doi.org/10.1145/1401890.1401926"
[WZ10]: <https://amstat.tandfonline.com/doi/pdf/10.1198/jasa.2009.tm08651?needAccess=true> "L. Wasserman and S. Zhou. (2010). A statistical framework for differential privacy. J. Amer. Stat. Assoc. [Online]. 105(489), pp. 375–389. Available: http://dx.doi.org/10.1198/jasa.2009.tm08651"
[CM06]: <http://cseweb.ucsd.edu/~kamalika/pubs/cm06.pdf> "K. Chaudhuri and N. Mishra. (2006, Aug.). Advances in Cryptology—CRYPTO 2006 (Lecture Notes in Computer Science Series, vol. 4117) [Online]. Available: http://dx.doi.org/10.1007/11818175_12"
[MKA+08]: <http://www.cse.psu.edu/~duk17/papers/PrivacyOnTheMap.pdf> "A. Machanavajjhala, D. Kifer, J. M. Abowd, J. Gehrke, and L. Vilhuber. (2008, June). Privacy: Theory meets practice on the map. presented at IEEE 24th Int. Conf. Data Engineering (ICDE) [Online]. Available: http://dx.doi.org/10.1109/ICDE.2008.4497436"
[CMS11]: <http://www.jmlr.org/papers/volume12/chaudhuri11a/chaudhuri11a.pdf> " K. Chaudhuri, C. Monteleoni, and A. D. Sarwate. (2011, Mar.). Differentially private empirical risk minimization. J. Mach. Learn. Res. [Online]. 12, pp. 1069–1109. Available: http://jmlr.csail.mit.edu/papers/v12/chaudhuri11a.html"
[RBH+12]: <https://arxiv.org/pdf/0911.5708.pdf> "B. I. P. Rubinstein, P. L. Bartlett, L. Huang, and N. Taft. (2012). Learning in a large function space: Privacy-preserving mechanisms for SVM learning. J. Privacy Confident. [Online]. 4(1), pp. 65–100. Available: http://repository.cmu.edu/jpc/vol4/iss1/4/"
[RHM+09]: <https://homes.cs.washington.edu/~suciu/pods59-rastogi.pdf> "V. Rastogi, M. Hay, G. Miklau, and D. Suciu. Relationship privacy: Output perturbation for queries with joins. presented at 28th ACM SIGMOD-SIGACTSIGART Symp. Principles Database Systems (PODS ’09) [Online]. Available: http://dx.doi.org/10.1145/1559795.1559812"
[KM11]: <http://www.cse.psu.edu/~duk17/papers/nflprivacy.pdf> "D. Kifer and A. Machanavajjhala. No free lunch in data privacy. presented at 2011 ACM SIGMOD Int. Conf. Management Data [Online]. Available: http://dx.doi.org/10.1145/1989323.1989345"
[DS09]: <https://utd.edu/~mxk055100/courses/crypto-for-dbsec10s_files/DworkSmith.pdf> "C. Dwork and A. Smith. (2009). Differential privacy for statistics: What we know and what we want to learn. J. Privacy Confident. [Online]. 1(2), pp. 135–154 [Online]. Available: http://repository.cmu.edu/jpc/vol1/iss2/2"
[LP12a]: <https://www.georgejpappas.org/papers/06606817.pdf> "J. Le Ny and G. J. Pappas. (2012, Dec.). Differentially private filtering. presented at 51st Conf. Decision and Control (CDC) [Online]. Available: http://dx.doi.org/10.1109/CDC.2012.6426355"
[LP12b]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=6483414> "J. Le Ny and G. J. Pappas. (2012, Oct.). Differentially private Kalman filtering. presented at 50th Annu. Allerton Conf. Communications, Control and Computing [Online]. Available: http://dx.doi.org/10.1109/Allerton.2012. 6483414"
[FX12]: <http://www.mathcs.emory.edu/aims/pub/realtime12cikm.pdf> "L. Fan and L. Xiong. Real-time aggregate monitoring with differential privacy. presented at 21st ACM Int. Conf. Information and Knowledge Management (CIKM ’12) [Online]. Available: http://dx.doi.org/10.1145/2396761.2398595"
[ZZX+12]: <http://vldb.org/pvldb/vol5/p1364_junzhang_vldb2012.pdf> "J. Zhang, Z. Zhang, X. Xiao, Y. Yang, and M. Winslett. (2012, Jul.). Functional mechanism: Regression analysis under differential privacy. in Proc. VLDB Endowment [Online]. 5(11), pp. 1364–1375. Available: http://vldb.org/pvldb/vol5/p1364_junzhang_vldb2012.pdf"
[CSS12]: <https://arxiv.org/pdf/1207.2812.pdf> "K. Chaudhuri, A. Sarwate, and K. Sinha, “Near-optimal algorithms for differentially-private principal components,”J. Mach. Learn. Res., to be published."
[HLM12]: <https://papers.nips.cc/paper/4548-a-simple-and-practical-algorithm-for-differentially-private-data-release.pdf> "M. Hardt, K. Ligett, and F. McSherry. (2012). Advances in Neural Information Processing Systems 25 [Online]. Available: http://books.nips.cc/papers/files/nips25/NIPS2012_1143.pdf"
[GR11]: <http://www.arpitaghosh.com/papers/ec053-ghosh.pdf> "A. Ghosh and A. Roth. Selling privacy at auction. presented at 12th ACM Conf. Electronic Commerce (EC ’11) [Online]. Available: http://dx.doi.org/10.1145/1993574.1993605"
[CH11]: <http://www.jmlr.org/proceedings/papers/v19/chaudhuri11a/chaudhuri11a.pdf> "K. Chaudhuri and D. Hsu. (2011, June). Proceedings of the 24th Annual Conference on Learning Theory (COLT ‘11) (JMLR Workshop and Conference Proceedings Series, vol. 19) [Online]. Available: http://www.jmlr.org/proceedings/papers/v19/chaudhuri11a/chaudhuri11a.pdf"
[DRV10]: <https://privacytools.seas.harvard.edu/files/privacytools/files/05670947.pdf> "C. Dwork, G. Rothblum, and S. Vadhan. (2010, Oct.). Boosting and differential privacy. presented at 51st Annu. IEEE Symp. Foundations Computer Science (FOCS ’10) [Online]. Available: http://dx.doi.org/10.1109/FOCS.2010.12"
[MT07]: <http://kunaltalwar.org/papers/expmech.pdf> "F. McSherry and K. Talwar. Mechanism design via differential privacy. presented at 48th Annu. IEEE Symp. Foundations Computer Science (FOCS ’07) [Online]. Available: http://dx.doi.org/10.1109/FOCS.2007.41"
[HR13]: <https://arxiv.org/pdf/1211.0975.pdf> "M. Hardt and A. Roth, “Beyond worst-case analysis in private singular vector computation,” in Proc. 45th Annu. ACM Symp. Theory Computing (STOC ’13), June 2013, New York."
[BDM+05]: <http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.126.209&rep=rep1&type=pdf> "A. Blum, C. Dwork, F. McSherry, and K. Nissim. Practical privacy: The SuLQ framework. presented at 24th ACM SIGMOD-SIGACT-SIGART Symp. Principles Database Systems (PODS ’05) [Online]. Available: http://dx.doi.org/10.1145/1065167.1065184"
[L11]: <http://www.stat.cmu.edu/~jinglei/mle_nips_unblinded_main.pdf> "J. Lei, “Differentially private M-estimators. (2011). Advances in Neural Information Processing Systems 24 [Online]. Available: http://books.nips.cc/papers/files/nips24/NIPS2011_0256.pdf"
[KST12]: <http://proceedings.mlr.press/v23/kifer12/kifer12.pdf> "D. Kifer, A. Smith, and A. Thakurta. (2012, June). Proceedings of the 25th Annual Conference on Learning Theory (COLT ’12) (JMLR Workshop and Conference Proceedings Series, vol. 23) [Online]. Available: http://jmlr.csail.mit.edu/proceedings/papers/v23/kifer12/kifer12.pdf"
[C11]: <http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.229.2638&rep=rep1&type=pdf> "G. Cormode. Personal privacy vs population privacy: Learning to attack anonymization. presented at 17th ACM SIGKDD Int. Conf. Knowledge Discovery and Data Mining (KDD ’11) [Online]. Available: http://dx.doi.org/10.1145/2020408.2020598"
[KT13]: <https://theory.epfl.ch/kapralov/papers/dp.pdf> "M. Kapralov and K. Talwar, “On differentially private low rank approximation,” in Proc. 24th Annu. ACM–SIAM Symp. Discrete Algorithms (SODA ‘13), New Orleans, LA, pp. 1395–1414."
[JKT12]: <http://www.jmlr.org/proceedings/papers/v23/jain12/jain12.pdf> "P. Jain, P. Kothari, and A. Thakurta. (2012, June). Proceedings of the 25th Annual Conference on Learning Theory (COLT ’12) (JMLR Workshop and Conference Proceedings Series, vol. 23) [Online]. Available: http://www.jmlr.org/proceedings/papers/v23/jain12/jain12.pdf"
[RN10]: <https://www.microsoft.com/en-us/research/wp-content/uploads/2009/11/paper.pdf> "V. Rastogi and S. Nath. Differentially private aggregation of distributed time-series with transformation and encryption. presented at 2010 ACM SIGMOD Int. Conf. Management Data [Online]. Available: http://dx.doi.org/10.1145/1807167.1807247"
[BKN10]: <https://www.cs.bgu.ac.il/~beimel/Papers/BKN.pdf> "A. Beimel, S. P. Kasiviswanathan, and K. Nissim. (2010, Feb. 9–11). Theory of Cryptography (Lecture Notes in Computer Science Series, vol. 5978) [Online]. Available: http://dx.doi.org/10.1007/978-3-642-11799-2_26"


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
