Download Link: https://assignmentchef.com/product/solved-ecse211-lab-2-odometry
<br>
The following design requirements must be met by your robot:




<strong>Odometer: </strong>




<ul>

 <li>Must determine the robot’s <strong>X</strong>​ , ​ ​<strong>Y</strong> and ​ <strong>θ</strong>​​</li>

 <li>Must display the ​ <strong>X</strong>​ ,​ ​ <strong>Y</strong>​ ​ and​​ <strong>θ</strong>​ ​ on the LCD display.​</li>

 <li><strong>X</strong> ​ and​ ​ <strong>Y</strong>​ ​ must be in cm.​</li>

</ul>




<ul>

 <li><strong>X</strong> ​ and​ ​ <strong>Y</strong>​ ​ can be negative.​</li>

 <li><strong>θ</strong> ​ must be in degrees.​</li>

 <li><strong>θ</strong> ​ must range from [0​ ⁰, 359.9⁰]:</li>

</ul>

○    When the value increases past 360⁰, it should return to 0⁰.

○    When the value decreases past 0⁰, it should wrap to 359.9⁰




<ul>

 <li>The zero values for (<strong>X</strong>​ ​, <strong>Y</strong>​ ​), i.e. (0,0), must respect the convention shown in Figure 3.​</li>

</ul>







<h1>Demonstration <sub>                               </sub></h1>

The design must satisfy the requirements by completing the demonstration outlined below.







<h2>Design presentation</h2>




Before demoing the design, your group will be asked some questions for less than 5 minutes. You will present your design and answer questions designed to test your individual understanding of the lab concepts. Each person will be graded individually.




You must present your workflow, an overview of the hardware design, and an overview of the software functionality. Visualizing software with graphics such as flow charts is valuable.




<h2>Float Motors</h2>




The TA will check whether the <strong>X</strong>​ ​, <strong>Y</strong>​ and <strong>θ</strong>​ values are updated correctly on the robot’s LCD screen by floating the robot’s motors/wheels.

<em> </em>

All three axes (<strong>X</strong>​ ,​ ​​<strong>Y</strong>,​ ​​<strong>θ</strong>)​ are checked:

<strong> </strong>

<ul>

 <li><strong>X </strong>&amp;​<strong> Y </strong>​ values work​            →  ​ <strong>5</strong>​<strong> points</strong></li>

 <li><strong>θ </strong>values work​ →  ​ <strong>5</strong>​<strong> points </strong></li>

</ul>

<strong> </strong>

<em>E.g.</em>​ if the (​<strong>X</strong>​, ​<strong>Y</strong>​, ​<strong>θ</strong>​) convention is set as in ​Figure 1, ​then:




<ul>

 <li>Moving both wheels <strong>forward</strong>​ should increase ​           <strong>Y</strong>​ .​</li>

 <li>Moving both wheels <strong>backward</strong>​ should decrease ​         <strong>Y</strong>​ .​</li>

 <li>Moving the right wheel <strong>backward</strong>​ and the left​      wheel <strong>forward </strong>​             simultaneously should increase​            <strong>θ</strong>.​</li>

 <li>Moving the right wheel <strong>forward</strong>​ ​ and the left wheel <strong>backward </strong>​simultaneously should decrease​ ​<strong>θ</strong>​.</li>

</ul>

<em> </em>

<strong><em>Figure 1: Robot faces north at 0</em></strong>​<strong><em><sup>o</sup></em></strong><sup>​</sup><strong><em>. </em></strong>

<em>E.g.</em>​ if the (​<strong>X</strong>​, ​<strong>Y</strong>​, ​<strong>θ</strong>​) convention is set as in ​Figure 2, ​then:




<ul>

 <li>Moving both wheels <strong>forward</strong>​ should increase ​           <strong>X</strong>​ .​</li>

 <li>Moving both wheels <strong>backward</strong>​ should decrease ​         <strong>X</strong>​ .​</li>

 <li>Moving the right wheel <strong>backward</strong>​ and the left​      wheel <strong>forward </strong>​             simultaneously should increase​            ​ <strong>θ</strong>​ .​</li>

 <li>Moving the right wheel ​<strong>forward</strong>​ and the left wheel <strong>backward </strong>​simultaneously should decrease​ ​<strong>θ</strong>​.</li>

</ul>

<strong><em>Figure 2: Robot faces east at 90</em></strong>​<strong><em><sup>o</sup></em></strong><sup>​</sup><strong><em>. </em></strong>

.













<table width="621">

 <tbody>

  <tr>

   <td width="432"> <strong><em> </em></strong><strong>Odometry Check </strong> </td>

   <td width="189"> </td>

  </tr>

 </tbody>

</table>

The TA will ask you to run your robot off the center of a tile, as shown by <strong>S</strong>​ in Figure 3. The robot should then follow the 3-by-3 tile square trajectory using SquareDriver​ .​ The robot should work using odometry. Throughout the demo, the TA will observe the reported (<strong>X</strong>​ ,​ <strong>Y</strong>​ ,​ <strong>θ</strong>​ ​) values on the robot’s LCD screen. When the robot stops at the final position (<strong>X</strong>​ F​ ,<sub>​ </sub><strong>Y</strong>​ F​ )<sub>​</sub> near <strong>S</strong>​ ,​ the final readings on the LCD screen (<strong>X</strong>​ ,​ <strong>Y</strong>​ ,​  <strong>θ</strong>​)​ are used to evaluate the odometer’s accuracy and calculate the <strong>error</strong>​ ​ <strong>distance </strong>​ϵ as:​

ϵ = √(<em>X </em>− <em>X<sub>F</sub></em>)<sup>2 </sup>+ (<em>Y </em>− <em>Y<sub>F</sub></em>)<sup>2</sup>




Note that the <strong>error</strong>​  ​ϵ​ is calculated as the ​Euclidean distance​ between:​




<ul>

 <li>The odometer’s readings (<strong>X</strong>​ ​,<strong>Y</strong>​ )​ , which signifies where the robot thinks it is with respect to</li>

</ul>

the origin <strong>(0,0)</strong>, and

​          ​

<ul>

 <li>The final actual position (<strong>X</strong>​ <strong>F</strong>​ ,<sub>​ </sub><strong>Y</strong>​ <strong>F</strong>​ )<sub>​ </sub>, which ideally should be the point <strong>S</strong>​ where the robot started​ the 3-by-3 tile square trajectory.</li>

</ul>




This means that it is <strong>not an issue</strong>​     if your robot does not return to the ​    ​<em>exact</em>​ starting point <strong>S</strong>​ , as​    long as the odometer reports a position that <strong>matches</strong>​           its real-world location.​







Point grid based on <sub>  </sub><strong>error</strong>​ ​ϵ​<strong><em>:</em></strong>​

<strong>[0, 3] cm</strong> <strong>→   </strong><strong>5</strong>​<strong> points</strong>

<strong>(3,</strong> <strong>6] cm</strong> <strong>→</strong> <strong>2.5 points</strong>

<strong>(6,</strong> <strong>∞) cm</strong> <strong>→</strong> <strong>0 points</strong>







Point grid based on the difference between the displayed <strong>θ</strong>​ and actual ​            <strong>θ</strong>​ :​

<strong>[0, 15] °</strong>     <strong>→   </strong><strong>5</strong>​<strong> points</strong>

<strong>(15,</strong> <strong>30] °</strong> <strong>→</strong> <strong>2.5 points</strong>

<strong>(30,</strong> <strong>∞) °</strong> <strong>→</strong> <strong>0 points</strong>



















<strong>(0, 0)</strong>

<strong>Figure 3. 3-by-3 tile trajectory using </strong><strong>SquareDriver.</strong>































<h1>Implementation instructions</h1>

<strong> </strong>

<ol>

 <li>In java​ , implement your odometer design in the ​       run()​ method of the​          Odometer class. This class is threaded and will run continuously when your robot is working.</li>

 <li>In java​ , tweak the values of ​  WHEEL_RAD​     and ​        BASE_WIDTH ​               so that your​      robot drives in a square pattern when calling SquareDriver.drive().​</li>

</ol>




<h1>Report Requirements</h1>




The following sections must be included in your report. Answer all questions in the lab report and copy them into your report. For more information, refer to the Lab Submission Instructions. Always provide justifications and explanations for all your answers.




<h2>Section 1: Design Evaluation</h2>




You should concisely explain the overall design of your software and hardware. You must present your workflow, an overview of the hardware design, and an overview of the software functionality. You must briefly talk about your design choices before arriving at your final design. Visualizing hardware and software with graphics (i.e. flowcharts, class diagrams) must be shown. The design evaluation section is expected to be within <strong>half a page</strong>​ (excluding graphics).​




<h2>Section 2: Test Data</h2>




This section describes what data must be collected to evaluate your design requirements. Collect the data using the methodology described below and present it in your report.




<strong>Odometer test </strong><sub>  </sub>(​ <em>10</em>​ <em> independent trials</em>​)

<ol>

 <li>Note the starting position <strong>S</strong>​ of the robot’s center and consider it to be ​ <strong>(0</strong>​        <strong>,0)</strong> for this trial.​</li>

 <li>Run the robot in a 3-by-3 square using java.​</li>

 <li>Measure its resulting signed <strong>X</strong>​ <strong>F</strong>​ and <sub>​ </sub><strong>Y</strong>​ ​<strong>F</strong> position with respect to its starting position <sub>​       </sub><strong>S</strong>​ .​ Note the reported values of <strong>X</strong>​ and ​         <strong>Y</strong>​ shown for the odometer.​</li>

</ol>







<h2>Section 3: Test Analysis</h2>




<strong>Present the following analysis in a table in your report</strong><sub>   </sub>

<ol>

 <li>Compute the Euclidean error distance​ ​ϵ​ of the position for each test.​</li>

 <li>Compute the mean and standard deviation for <strong>X</strong>​ ,​ <strong>Y</strong>​ ​, and ϵ​​. That means, you need to perform 3 mean and 3 standard deviation calculations in total. Use the sample standard deviation formula. Show one sample calculation for both mean and standard deviation formulas.</li>

</ol>

.




<strong>Answer the following questions in your report </strong>

<strong> </strong>

<ol>

 <li>What does the standard deviation of X, Y and ϵ tell you about the accuracy of the odometer? What causes changes in standard deviation?</li>

</ol>




<ol start="2">

 <li>What is the sampling frequency of your odometer (i.e. the frequency at which the tacho count is measured)? What is the tradeoff of having a high sampling frequency versus a low sampling frequency?</li>

</ol>




<h2>Section 4: Observations and Conclusions</h2>




<ul>

 <li>Is the error you observed in the odometer tolerable for larger distances? What happens if the robot travels 5 times the 3-by-3 grid’s distance?</li>

</ul>




<ul>

 <li>Do you expect the odometer’s error​ to grow linearly with respect to travel distance? Why?​</li>

</ul>




<h2>Section 5: Further Improvements</h2>




<ul>

 <li>Propose a means of reducing the slip of the robot’s wheels using software.</li>

 <li>Propose a means of improving the accuracy of the odometer using one or more light</li>

</ul>

sensors.


