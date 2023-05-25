# Project
In physics class, the cars we have kinda suck. They look ugly, are hard to measure, move at a very weird speed, and are inconsistent. We're making a car that will fix all those problems.

### Requirements
- able to control the velocity on many levels (measurable through initial completion and quantity of options)
- maintain a constant velocity regardless of battery charge (measurable through practical testing)
- reasonable size (measurable by Mr Manning's standards)
- sturdy (measurable through various durability tests)
- easily replaceable battery (measurable by Mr Manning's standards)

### Possible additions for after we're done
- kill switch after a certain distance
- constant acceleration (measurable through initial completion and quantity of options)
- looks cool (measurable by Mr Manning's standards)
- collects data and gives feedback (measurable through initial completion and types of data)

# Timeline
- November 2022: initial plan for wiring and coding
- December 2022: prototype
- February 2023: final plan for wiring and coding
- May 2023: done

## Materials
- Arduino Metro 328
- acrylic for laser cutting the body and gears (available)
- 3d printing material for anything that can't be laser cut (available hopefully)
- 4 60mm micro servo wheels (available)
- 2 TT motors for the axles (available)
- power switch and indicator
- go button

### Total Budget
everything is availiable in the lab

### Results
We plan to build 1 cart initially but document it enough to be able to fully replicate it

## Appearance
25cm x 12.5cm x 5cm, smooth boxy design, bright orange color because it looks cool
### in CAD:
![image](https://user-images.githubusercontent.com/55702245/235510775-9de12c3a-202d-4524-87b9-7f411ca9a8ea.png)
### In person:
![IMG_1387](https://github.com/cmillar70/complexcar/assets/60944294/bd59fa34-2048-4bc4-9e9b-20b942849c50)
## Wiring
![wiring](https://github.com/cmillar70/complexcar/assets/60944294/7382f88a-d9e9-48a5-95e8-93abce43da84)

## Code

```python
void setup() {
  // put your setup code here, to run once:

  Serial.begin(9600);
  pinMode(5, OUTPUT);
  pinMode(9, INPUT_PULLUP); 
  // reads when the four spokes attached to the motor crosses a photo-interuptor
  pinMode(10, OUTPUT);
  pinMode(11, OUTPUT);
  // sets speed of motors
  Serial.println("In setup!");
}
int now = 0;
int pre = 0;
int myTime = 0;
int mySpeed = 0;
int button = 0;
int onoff = 0;
void loop() {
  digitalWrite(5, HIGH);
  digitalWrite(4, LOW);
  // tells this motor to go relatively forward as fast as it can go
  analogWrite(11, 255);
  analogWrite(10, 0);
// tells another motor to go relatively backward as fast as it can go
  int bus = millis();
  while (millis() < bus + 4000) // tells the car to run for 4 seconds
  {
    onoff = digitalRead(9);
    if (onoff == 1) // checks if one of the four spokes passes the photo interrupter
    {
      now = millis();
      Serial.println(now - pre); // prints the time elapsed between the last blockage of the PI
      pre = now; //resets the clock~
      while (onoff == 1)
      {
        onoff = digitalRead(9); // the while loop iterates nothing happening until the photointeruptor is no longer blocked.
      }
    }
  }
}

```
## Test Procedures
place car down, put batteries in. let it run for its full duration. afterwords, check the serial monitor to see if the time is consistant.
##
# Daily Log
- 4/28: physical car is complete
- 2/15: adding cones to axles to hold them in place
- 2/13: finishing gear adjustments
- 2/6-2/10: making gears, moving motors, and making motor mounts
- 2/3: submitting goal schedule for Q3
- 1/16-1/19: working on mid-year presentation
- 1/13: resizing car to make it longer
- 1/12: assembled first laser cut car
- 11/17: improving goals for thanksgiving and winter break
- 11/4-11/15: setting up wiring and coding
- 11/3: set goals for thanksgiving break and winter break
- 10/31: created holes for the axles
- 10/20-10/26: presentation feedback response
- 10/19: presentation successful
- 10/10-10/17: presentation editing
- 10/5-10/7: starting project presentation
- 10/3: assembled a set of wheels and started working on a gear
- 9/30: taking note of what we've accomplished this week and creating this log
- 9/29: browsing parts we can use and other projects for ideas
- 9/28: cracking open a constant velocity car to see how it works and brainstorming for our own car

