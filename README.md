# Evaluation of parameters for CMOS Inverter using 7nm Finfet Technology(ASAP 7nm PDK)


#### Inverter Code-
```
** sch_path: /home/hprcse/Finfet/inverter_finfet.sch
**.subckt inverter_finfet
Xpfet1 nfet_out nfet_in vdd vdd asap_7nm_pfet l=7e-009 nfin=14
Xnfet1 nfet_out nfet_in GND GND asap_7nm_nfet l=7e-009 nfin=14
V1 nfet_in GND pulse(0 0.7 20p 10p 10p 20p 500p 1)
V2 vdd GND 0.7
**** begin user architecture code


.tran 0.1p 100p
.control
    run
    set xbrushwidth=3
    plot nfet_out nfet_in
.endc


**** end user architecture code
**.ends
.GLOBAL GND
**** begin user architecture code

.subckt asap_7nm_pfet S G D B l=7e-009 nfin=14
	npmos_finfet S G D B BSIMCMG_osdi_P l=7e-009 nfin=14
.ends asap_7nm_pfet

.model BSIMCMG_osdi_P BSIMCMG_va (
+ TYPE = 0

************************************************************
*                         general                          *
************************************************************
+version = 107             bulkmod = 1               igcmod  = 1               igbmod  = 0
+gidlmod = 1               iimod   = 0               geomod  = 1               rdsmod  = 0
+rgatemod= 0               rgeomod = 0               shmod   = 0               nqsmod  = 0
+coremod = 0               cgeomod = 0               capmod  = 0               tnom    = 25
+eot     = 1e-009          eotbox  = 1.4e-007        eotacc  = 3e-010          tfin    = 6.5e-009
+toxp    = 2.1e-009        nbody   = 1e+022          phig    = 4.9278          epsrox  = 3.9
+epsrsub = 11.9            easub   = 4.05            ni0sub  = 1.1e+016        bg0sub  = 1.17
+nc0sub  = 2.86e+025       nsd     = 2e+026          ngate   = 0               nseg    = 5
+l       = 2.1e-008        xl      = 1e-009          lint    = -2.5e-009       dlc     = 0
+dlbin   = 0               hfin    = 3.2e-008        deltaw  = 0               deltawcv= 0
+sdterm  = 0               epsrsp  = 3.9             nfin    = 1
+toxg    = 1.8e-009
************************************************************
*                            dc                            *
************************************************************
+cit     = 0               cdsc    = 0.003469        cdscd   = 0.001486        dvt0    = 0.05
+dvt1    = 0.36            phin    = 0.05            eta0    = 0.094           dsub    = 0.24
+k1rsce  = 0               lpe0    = 0               dvtshift= 0               qmfactor= 0
+etaqm   = 0.54            qm0     = 2.183e-012      pqm     = 0.66            u0      = 0.0237
+etamob  = 4               up      = 0               ua      = 1.133           eu      = 0.05
+ud      = 0.0105          ucs     = 0.2672          rdswmin = 0               rdsw    = 200
+wr      = 1               rswmin  = 0               rdwmin  = 0               rshs    = 0
+rshd    = 0               vsat    = 60000           deltavsat= 0.17            ksativ  = 1.592
+mexp    = 2.491           ptwg    = 25              pclm    = 0.01            pclmg   = 1
+pdibl1  = 800             pdibl2  = 0.005704        drout   = 4.97            pvag    = 200
+fpitch  = 2.7e-008        rth0    = 0.15            cth0    = 1.243e-006      wth0    = 2.6e-007
+lcdscd  = 0               lcdscdr = 0               lrdsw   = 1.3             lvsat   = 1441
************************************************************
*                         leakage                          *
************************************************************
+aigc    = 0.007           bigc    = 0.0015          cigc    = 1               dlcigs  = 5e-009
+dlcigd  = 5e-009          aigs    = 0.006           aigd    = 0.006           bigs    = 0.001944
+bigd    = 0.001944        cigs    = 1               cigd    = 1               poxedge = 1.152
+agidl   = 2e-012          agisl   = 2e-012          bgidl   = 1.5e+008        bgisl   = 1.5e+008
+egidl   = 1.142           egisl   = 1.142
************************************************************
*                            rf                            *
************************************************************
************************************************************
*                         junction                         *
************************************************************
************************************************************
*                       capacitance                        *
************************************************************
+cfs     = 0               cfd     = 0               cgso    = 1.6e-010        cgdo    = 1.6e-010
+cgsl    = 0               cgdl    = 0               ckappas = 0.6             ckappad = 0.6
+cgbo    = 0               cgbl    = 0
************************************************************
*                       temperature                        *
************************************************************
+tbgasub = 0.000473        tbgbsub = 636             kt1     = 0               kt1l    = 0
+ute     = -1.2            utl     = 0               ua1     = 0.001032        ud1     = 0
+ucste   = -0.004775       at      = 0.001           ptwgt   = 0.004           tmexp   = 0
+prt     = 0               tgidl   = -0.007          igt     = 2.5
************************************************************
*                          noise                           *
************************************************************
**)
.control
pre_osdi /home/hprcse/Documents/test/bsimcmg.osdi
.endc



.subckt asap_7nm_nfet S G D B l=7e-009 nfin=14
	nnmos_finfet S G D B BSIMCMG_osdi_N l=7e-009 nfin=14
.ends asap_7nm_nfet

.model BSIMCMG_osdi_N BSIMCMG_va (
+ TYPE = 1
************************************************************
*                         general                          *
************************************************************
+version = 107             bulkmod = 1               igcmod  = 1               igbmod  = 0
+gidlmod = 1               iimod   = 0               geomod  = 1               rdsmod  = 0
+rgatemod= 0               rgeomod = 0               shmod   = 0               nqsmod  = 0
+coremod = 0               cgeomod = 0               capmod  = 0               tnom    = 25
+eot     = 1e-009          eotbox  = 1.4e-007        eotacc  = 1e-010          tfin    = 6.5e-009
+toxp    = 2.1e-009        nbody   = 1e+022          phig    = 4.2466          epsrox  = 3.9
+epsrsub = 11.9            easub   = 4.05            ni0sub  = 1.1e+016        bg0sub  = 1.17
+nc0sub  = 2.86e+025       nsd     = 2e+026          ngate   = 0               nseg    = 5
+l       = 2.1e-008        xl      = 1e-009          lint    = -2e-009         dlc     = 0
+dlbin   = 0               hfin    = 3.2e-008        deltaw  = 0               deltawcv= 0
+sdterm  = 0               epsrsp  = 3.9             nfin    = 1
+toxg    = 1.80e-009
************************************************************
*                            dc                            *
************************************************************
+cit     = 0               cdsc    = 0.01            cdscd   = 0.01            dvt0    = 0.05
+dvt1    = 0.47            phin    = 0.05            eta0    = 0.07            dsub    = 0.35
+k1rsce  = 0               lpe0    = 0               dvtshift= 0               qmfactor= 2.5
+etaqm   = 0.54            qm0     = 0.001           pqm     = 0.66            u0      = 0.0303
+etamob  = 2               up      = 0               ua      = 0.55            eu      = 1.2
+ud      = 0               ucs     = 1               rdswmin = 0               rdsw    = 200
+wr      = 1               rswmin  = 0               rdwmin  = 0               rshs    = 0
+rshd    = 0               vsat    = 70000           deltavsat= 0.2             ksativ  = 2
+mexp    = 4               ptwg    = 30              pclm    = 0.05            pclmg   = 0
+pdibl1  = 0               pdibl2  = 0.002           drout   = 1               pvag    = 0
+fpitch  = 2.7e-008        rth0    = 0.225           cth0    = 1.243e-006      wth0    = 2.6e-007
+lcdscd  = 5e-005          lcdscdr = 5e-005          lrdsw   = 0.2             lvsat   = 0
************************************************************
*                         leakage                          *
************************************************************
+aigc    = 0.014           bigc    = 0.005           cigc    = 0.25            dlcigs  = 1e-009
+dlcigd  = 1e-009          aigs    = 0.0115          aigd    = 0.0115          bigs    = 0.00332
+bigd    = 0.00332         cigs    = 0.35            cigd    = 0.35            poxedge = 1.1
+agidl   = 1e-012          agisl   = 1e-012          bgidl   = 10000000        bgisl   = 10000000
+egidl   = 0.35            egisl   = 0.35
************************************************************
*                            rf                            *
************************************************************
************************************************************
*                         junction                         *
************************************************************
************************************************************
*                       capacitance                        *
************************************************************
+cfs     = 0               cfd     = 0               cgso    = 1.6e-010        cgdo    = 1.6e-010
+cgsl    = 0               cgdl    = 0               ckappas = 0.6             ckappad = 0.6
+cgbo    = 0               cgbl    = 0
************************************************************
*                       temperature                        *
************************************************************
+tbgasub = 0.000473        tbgbsub = 636             kt1     = 0               kt1l    = 0
+ute     = -0.7            utl     = 0               ua1     = 0.001032        ud1     = 0
+ucste   = -0.004775       at      = 0.001           ptwgt   = 0.004           tmexp   = 0
+prt     = 0               tgidl   = -0.007          igt     = 2.5
************************************************************
*                          noise                           *
************************************************************
**)
.control
pre_osdi /home/hprcse/Documents/test/bsimcmg.osdi
.endc


**** end user architecture code
.end

```
## Calculation of Different Parameter

#### Drain Current

Replace the analysis code part by this-
```
.dc v1 0 0.7 1m 
.control
    run
    set xbrushwidth=3
    plot -(v2#branch)
.endc
```
> Click on the peak to get the value on terminal
![image](https://github.com/user-attachments/assets/be500c57-0923-4b7f-a4df-4585aa969c69)


#### Propagation Delay
Propagation delay is the time it takes for a signal to propagate through a circuit from input to output.
tpd = (tphl + tplh) / 2
- **tphl**: Propagation delay for the transition from high to low.
- **tplh**: Propagation delay for the transition from low to high.
Here we are doing transient analysis as we want to simulate behaviour of Inverter over a period of Time
Replace the given code in analysis section-
```
.tran 1n 20n
.measure tran tplh trig v(nfet_in) val=0.35 fall=1 targ v(nfet_out) val=0.35 rise=1
.measure tran tphl trig v(nfet_in) val=0.35 rise=1 targ v(nfet_out) val=0.35 fall=1


.control
    run
    set xbrushwidth=3
    plot nfet_out nfet_in
    print tplh tphl
.endc
```
For Tutorial Link Refer- `https://youtu.be/alV15XE67oo?feature=shared`


#### Gain (Av)
Gain (Av) is the ratio of the output signal amplitude to the input signal amplitude in a circuit.
Av = Vout / Vin

- **Vout**: Output voltage.
- **Vin**: Input voltage.
Replace the given code in analysis section-

```
.dc v1 0 0.7 1m 
.control
    run
    set xbrushwidth=3
    *plot nfet_out nfet_in
    let gain=abs(deriv(nfet_out))
    meas dc peak_gain max gain
    plot gain
    print peak_gain
.endc
```

> You can click on the peak value on Gain graph or get the max value of gain in console by the code above
![image](https://github.com/user-attachments/assets/a5010684-c1f0-4baf-b9c2-4c2a6f21001a)


### Noise Margin
Noise margin is the measure of a digital circuit's ability to tolerate noise without misinterpreting logic levels.

- **Vil**: Maximum input voltage interpreted as a logic low.
- **Voh**: Minimum output voltage interpreted as a logic high.
- **Vih**: Minimum input voltage interpreted as a logic high.
- **Vol**: Maximum output voltage interpreted as a logic low.
> Calculate the points by clicking on it or check the console for values
![Add a little bit of body text](https://github.com/user-attachments/assets/ec00e79c-5ee6-4b5b-9398-e68617e50574)

### Output Resistance (Ro)
Output resistance (Ro) is the resistance seen by the load connected to the output of a circuit.

Ro = ΔVout / ΔIout
- **Vout**: Output voltage.
- **Iout**: Output current.
Replace the given code in analysis section-
```
.dc v1 0 0.7 1m 
.control
    run
    set xbrushwidth=3
    let gain=(abs(deriv(nfet_out)) >=1)*0.7
    *plot gain nfet_out nfet_in
    meas dc Vil find nfet_in when gain=nfet_out cross=1
    meas dc Voh find nfet_out when gain=nfet_out cross=1
    meas dc Vih find nfet_in when gain=nfet_out cross=2
    meas dc Vol find nfet_out when gain=nfet_out cross=2
    let nmh= Voh-Vih
    let nml= Vil-Vol
    print nmh
    print nml
.endc
```

> Click on the peak point to calculate output resistance
![image](https://github.com/user-attachments/assets/ec77e459-ef31-4bba-8fdd-ad5a3cf6ee76)

### Frequency (f)
Frequency (f) is the rate at which a periodic signal repeats, determined by the propagation delays of a circuit.

f = 1 / (tphl + tplh)
- **tphl**: Propagation delay for the transition from high to low.
- **tplh**: Propagation delay for the transition from low to high.
Use values of tphl and tplh from Propagation Delay Calculations

### Voltage Transfer Characteristic (VTC) of CMOS Inverter
The Voltage Transfer Characteristic (VTC) of a CMOS inverter describes the relationship between the input voltage (Vin) and the output voltage (Vout), illustrating how the inverter switches states.

- **Vin**: Input voltage applied to the inverter.
- **Vout**: Output voltage from the inverter.

The VTC curve typically features three regions: the cutoff region, the saturation region, and the linear region, depicting the inverter's behavior during the transition from logic low to logic high.
Replace the given code in analysis section-
```
.dc v1 0 0.7 1m 
.control
    run
    set xbrushwidth=3
    plot nfet_out nfet_in
    meas dc v_th when nfet_out=nfet_in
.endc
```

![image](https://github.com/user-attachments/assets/1218f987-fcdf-4ea3-bb6a-d1f5436e9378)


#### Power Dissipation
The output waveform mirrors the input, transitioning between 0V and VDD (0.7V).
- **Charging Phase**: The output rises to 0.7V during the first half of the period (10ps).
- **Discharging Phase**: The output drops back to 0V in the second half of the period (10ps).

#### Power Dissipation Visualization

- **Area under the Curve**: The power dissipation can be visualized as the area under the output voltage waveform when charging the load capacitor. 
For pulse change the values as follows-
```
pulse(0 0.7 0p 0.1p 0.1p 5p 10p 2)
```

Replace the given code in analysis section-
```
.tran 0.1p 40p
.control
    run
    set xbrushwidth=3
    let Id=v2#branch
    meas tran p integ Id from=10e-12 to=20e-12
    let pow=p*0.7*1e11
    print pow
.endc
** For 0.5fF Capacitor
```



> Here we can see charging and discharging of capacitor at the output
![image](https://github.com/user-attachments/assets/9c6c8462-4364-430e-95d8-680ee0571b28)
> We can observe oscillations happening in the current branch of VDD 
![image](https://github.com/user-attachments/assets/1dc64755-4f7b-4084-8e3f-1cae6778c4fe)
> We can se the spikes in current when there is transition of input output
![image](https://github.com/user-attachments/assets/1d5f23ca-77d6-4ad8-a277-707a6ab5a549)
**All above calculations are done for 0.1fF capacitor Load**



#### Transconductance (gm)
Transconductance (gm) measures the change in drain current (Id) with respect to the change in gate-source voltage (Vgs).
gm = dId / dVgs
For it's analysis we need a dc source instead on pulse and need to do dc analysis
Replace this code for it-
```
.dc v1 0 0.7 0.01
.control
    run
    set xbrushwidth=3

    * Calculate the current through the transistor
    let Id = v2#branch 

    * Calculate the transconductance as d(Id)/d(vin)
    let gm = real(deriv(Id, nfet_in))
    meas dc peak_gm MAX gm
    *plot gm  *Uncomment this line to see graph
    
    print peak_gm

.endc
```
> Calculate the Peak Value by clicking on peak point
![image](https://github.com/user-attachments/assets/82b86bd0-97b8-4a29-bc26-9b3be1e8493f)


