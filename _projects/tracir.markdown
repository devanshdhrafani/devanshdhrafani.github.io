---
layout: article
title: Autonomous Ultrasound-guided Needle Insertion for Battlefield Trauma Care
img: /assets/images/projects/tracir/tracir-mechanism-cropped.jpg
tags: 
    - Surgical Robots
    - Embedded systems
    - Robotics
select: true
excerpt: Novel vessel puncture recognition device validated on experiments in surgical pig labs.
date: 2022-10-31
---

Urgent care in case of high-tempo, traumatic scenarios like battlefield is paramount in saving a soldier's life. Sooner the care is provided, higher is the chance of recovery. One way to provide immediate care in traumatic situations is by administering drugs directly into the patient's Femoral vessels. Presently, this operation is performed by medical professionals. In battlefield, there is a lack on medical professionals, and thus an autonomous robotic needle insertion into patient's vessels can make the difference between life and death.

Designing an autonomous needle insertion system poses challenges such as modeling needle dynamics in various scenarios (outside skin, on skin surface, inside skin), accounting for skin movement during patient breathing, preventing excessive force causing vessel penetration, and addressing needle slippage leading to hematoma formation. To address these issues, we create a control law using force feedback at the needle tip, modeling needle dynamics in different scenarios, and incorporating vessel geometry using segmentation networks on Ultrasound image for precise insertion. Additionally, we build a puncture detection module with optical and pressure sensors to provide redundancy to the needle insertion segmentation network. 

![Needle Insertion Mechanism](/assets/images/projects/tracir/tracir-mechanism.jpeg?style=centerme){:.image--xxl}

My key contributions to this project are as follows:
- Researched a vessel puncture recognition system utilizing pressure and optical sensing and PSoC based data acquisition unit to provide redundancy to segmentation stack.
- Led a team of 3 to design, fabricate and test system.
- Integrated vessel puncture recognition device to the needle insertion stack. 
- Participated in pig surgical labs to test mechanism/pipeline and obtain feedback from UPMC doctors.


## Needle Insertion pipeline
Before talking about the puncture recognition system, let me give context by explaining the needle insertion pipeline. The system consists of a Universal Robots UR3E arm, an Ultrasound (US) Probe and the needle insertion mechanism. The probe and insertion mechanism are attached to the robot's end effector. Talking about the pipeline, we first do an US scan of the patient. The vessel segmentation and reconstruction pipeline then reconstructs the vessels and gives a 3D reconstruction of the vessels. Then, a suitable insertion location is selected and the robot moves to that position. Finally, the needle is inserted into the patient. The puncture recognition system monitors the needle's progress in the tissue by measuring the pressure at the needle tip and a looking for blood flashback using an optical sensor. On successful puncture, a guide-wire is inserted and then a catheter is placed on the vessel. Drugs can them be administered to the patient. 

![Autonomous Needle Insertion pipeline](/assets/images/projects/tracir/tracir-pipeline.png?style=centerme)
<div>{%- include extensions/youtube.html id='d2cXhW5H3oM' -%}</div>


## Puncture recognition system
The Ultrasound-derived needle position serves as an approximation of the actual needle placement. Through rigorous testing in pig surgical labs, we have observed that solely relying on visual inspection of the Ultrasound image is insufficient to verify a successful puncture. The implementation of a redundant system, capable of detecting successful vessel puncture and distinguishing between artery and vein punctures, proves indispensable for autonomous operations. The key requirements for this system include:
- Predicting the success or failure of vessel puncture.
- Classifying the needle position as either in the artery or vein.
- Surgically sealed module housing all electronic components.
- Disposable module containing one-time use medical components.

Taking into account all the requirements, the following system was designed. The sensing is achieved with an arterial pressure transducer and a tube liquid optical sensor. Output from the optical sensor serves as the first confirmation of puncture as it looks for blood flash. When inserting in arteries, due to the high blood pressure, as soon as the needle punctures the vessel, we see a blood flash. In veins, we use a syringe to draw out blood. The pressure sensor serves a dual purpose: detecting vessel puncture and identifying vein vs artery. The rhythmic pressure change indicates successful vessel puncture whereas the mean vessel pressure helps classify vein vs artery. 

For the design, we opted to go for a 2-part configuration. The bottom half of the system is a disposable module, consisting of tubes, syringes, pressure transducers which are all disposed after an operation to ensure sterile conditions. The top half is the reusable module, consisting of all the actuation, microcontrollers, and optical sensor. This part is surgically bagged to prevent contamination from the disposable module. a PSoC 5LP microcontroller is used for sensing and actuation. Below is the proposed design of the full system.

![Puncture Recognition system design](/assets/images/projects/tracir/ppr-design.png?style=centerme){:.image--xxl}

## Testing at pig surgical labs
To test the individual sensor subsystems on live needle insertions at UPMC pig surgical labs, we created 2 sensing packets - one for the pressure transducer and another for the optical sensor. Both were connected to a FreeSoC 2 - PSoC 5LP board. The sensing packets communicated via Serial to a ROS node on our base station. This ROS node would monitor the pressure and optical sensor to predict puncture and classify vessel. 

![Sensor subsystems testing kit](/assets/images/projects/tracir/ppr-phase-one-kits.jpg?style=centerme){:.image--xxxl}

After multiple insertions at pig surgical labs, we observed the pressure transducer give accurate estimate of the pig heart-rate when needle was inserted in the artery. For the vein, we observed a steady rhythmic beat corresponding to the respiratory rate.

![Arterial Insertion Pressure plot](/assets/images/projects/tracir/arterial-pressure.png?style=centerme){:.image--xxxl}

We performed a Fourier analysis on the time-domain pressure signal. The classification was then done based on the dominant frequencies and mean pressure from the frequency domain data.

![Fourier analysis of pressure data](/assets/images/projects/tracir/artery-fourier-analysis.png?style=centerme){:.image--xxxl}
![Vessel classification based on fourier analysis](/assets/images/projects/tracir/fourier-vessel-classify.png?style=centerme){:.image--xxxl}

## Conclusion
In conclusion, our autonomous ultrasound-guided needle insertion system represents a vital advancement in battlefield trauma care, addressing the critical need for immediate, life-saving interventions in the absence of sufficient medical professionals. Overcoming challenges in needle dynamics and safety, our system incorporates a redundant puncture recognition module utilizing pressure and optical sensors. Through rigorous testing in pig surgical labs, we successfully confirmed vessel puncture and achieved high-precision classification. The two-part modular design ensures sterility and practicality. 

This project has been an enriching learning journey, with the pivotal experience being my active involvement in pig surgical labs at UPMC. Testing our insertion mechanism and puncture detection system on live pigs provided a unique and invaluable insight into the intricate world of surgical robotics. I cultivated a profound appreciation for maintaining a sterile environment, meticulous component bagging to prevent contamination, and adherence to stringent surgical protocols. Beyond the operating room, the experience extended to thorough system evaluation for deployment readiness and rigorous testing of individual subsystems. Valuable feedback from surgeons on our insertion procedure and vessel puncture recognition system further enhanced the learning process. Additionally, this project refined my CAD design skills and deepened my proficiency with embedded platforms like the PSoC.

**Disclaimer**: Please note that all images and videos showcased on this page are the exclusive property of the [Biorobotics Lab](https://biorobotics.ri.cmu.edu/index.php){:target="\_blank"}. Any unauthorized use, reproduction, or distribution of these visual assets is strictly prohibited without the explicit consent of the Biorobotics Lab.
{:.warning}