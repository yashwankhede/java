public class Clock {

   private int hr; //store hours
   private int min; //store minutes
   private int sec; //store seconds

   // Default constructor

   public Clock () {
      setClock (0, 0, 0);
   }

   public Clock (int hours, int minutes, int seconds) {
      setClock (hours, minutes, seconds);
   }

   public void setClock (int hours, int minutes, int seconds) {
      if (0 <= hours && hours < 24)
         hr = hours;
      else
         hr = 0;
      if (0 <= minutes && minutes < 60)
         min = minutes;
      else
         min = 0;
      if (0 <= seconds && seconds < 60)
         sec = seconds;
      else
         sec = 0;
   }

   public int getHours() {
      return hr;
   }

   public int getMinutes() {
      return min;
   }

   public int getSeconds() {
      return sec;
   }

   public void addClock( Clock secondClock ) {
      this.sec += secondClock.getSeconds();
      this.min += secondClock.getMinutes();
      //add overflow to minutes from seconds
      this.min +=(int)(this.sec/60);
      //update seconds 
      this.sec = this.sec % 60;
      this.hr += secondClock.getHours();
      //add overflow to minutes from seconds
      this.hr +=(int)(this.min/60);
      //update minutes
      this.min = this.min % 60;
      //adjust hours
      this.hr = this.hr % 24;
   }

   public void tick(){
      this.sec += 1;
      //add overflow to minutes from seconds
      this.min +=(int)(this.sec/60);
      //update seconds 
      this.sec = this.sec % 60;
      //add overflow to minutes from seconds
      this.hr +=(int)(this.min/60);
      //update minutes
      this.min = this.min % 60;
      //adjust hours
      this.hr = this.hr %24;
   }

   public void tickDown(){
      this.sec -= 1;
      if(this.sec <0){
         this.sec+=60;
         this.min-=1;
      }
      if(this.min<0){
         this.min+=60;
         this.hr-=1;
      }
      if(this.hr<0){
         this.hr+=24;
      }
   }
}