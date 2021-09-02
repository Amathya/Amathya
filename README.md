<app-employeelayout>
  </app-employeelayout>
  <div style="background-color:cornsilk" class="container">
    <h1 style="text-align:center">Add Hotel</h1>
    <div style="text-align:center;margin-left:20em">
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; *All fileds are manadatory
    </div>

    <div class="row">
      <div class="col-md-4">
      </div>
      <div class="col-md-4">
        <form [formGroup]="HotelForm" (ngSubmit)="SubmitForm(HotelForm)">
          <div class="form-group">
            <label>Hotel Name</label>
            <input type="text" class="form-control" placeholder="Enter the Hotel name" formControlName="HotelName">
            <p *ngIf="HotelForm.controls.HotelName.errors?.required && HotelForm.controls.HotelName.touched"
               class="alert alert-danger">This field is required!</p>
            <p *ngIf="HotelForm.controls.HotelName.errors?.pattern && HotelForm.controls.HotelName.touched "
               style="color:red" class="alert alert-danger">Only Alphabets are allowed!</p>
          </div>
          <div class="form-group">
            <label>Hotel Rating</label>
            <select class="form-control" formControlName="HotelRating" placeholder="--Hotel Rating--">
              <option>--Hotel Rating--</option>
              <option value="2-star">2-Star</option>
              <option value="3-star">3-Star</option>
              <option value="4-star">4-Star</option>
              <option value="5-star">5-Star</option>
            </select>
          </div>
          <div class="form-group">
            <label>Single Room Price(INR)</label>
            <input type="number" class="form-control" placeholder="Enter price of single room" formControlName="SingleRoomPrice">
            <p *ngIf="HotelForm.controls.SingleRoomPrice.errors?.required &&  HotelForm.controls.SingleRoomPrice.touched"
               class="alert alert-danger" style="color:red">This field is required!</p>
            <p *ngIf="HotelForm.controls.SingleRoomPrice.errors?.pattern  && HotelForm.controls.SingleRoomPrice.touched"
               style="color:red" class="alert alert-danger">only numbers are allowed!</p>
          </div>
          <div class="form-group">
            <label>Double Room Price(INR)</label>
            <input type="number" class="form-control" placeholder="Enter price of double room" formControlName="DoubleRoomPrice">
            <p *ngIf="HotelForm.controls.DoubleRoomPrice.errors?.required &&  HotelForm.controls.DoubleRoomPrice.touched"
               class="alert alert-danger" style="color:red">This field is required!</p>
            <p *ngIf="HotelForm.controls.DoubleRoomPrice.errors?.pattern  && HotelForm.controls.DoubleRoomPrice.touched"
               style="color:red" class="alert alert-danger">only numbers are allowed!</p>
          </div>
          <div class="form-group">
            <label>Deluxe Room Price(INR)</label>
            <input type="number" class="form-control" placeholder="Enter price of deluxe room" formControlName="DeluxeRoomPrice">
            <p *ngIf="HotelForm.controls.DeluxeRoomPrice.errors?.required &&  HotelForm.controls.DeluxeRoomPrice.touched"
               class="alert alert-danger" style="color:red">This field is required!</p>
            <p *ngIf="HotelForm.controls.DeluxeRoomPrice.errors?.pattern  && HotelForm.controls.DeluxeRoomPrice.touched"
               style="color:red" class="alert alert-danger">only numbers are allowed!</p>
          </div>
          <div class="form-group">
            <label>Suite Price(INR)</label>
            <input type="number" class="form-control" placeholder="Enter price of suite" formControlName="SuitePrice">
            <p *ngIf="HotelForm.controls.SuitePrice.errors?.required &&  HotelForm.controls.SuitePrice.touched"
               class="alert alert-danger" style="color:red">This field is required!</p>
            <p *ngIf="HotelForm.controls.SuitePrice.errors?.pattern  && HotelForm.controls.SuitePrice.touched"
               style="color:red" class="alert alert-danger">only numbers are allowed!</p>
          </div>
          <div class="form-group">
            <label>City</label>
            <input type="text" class="form-control" placeholder="Enter the city name" formControlName="City">
            <p *ngIf="HotelForm.controls.City.errors?.required &&  HotelForm.controls.City.touched"
               style="color:red" class="alert alert-danger">&nbsp;This field is required!</p>
            <p *ngIf="HotelForm.controls.City.errors?.pattern && HotelForm.controls.City.touched "
               style="color:red" class="alert alert-danger">Only Alphabets are allowed!</p>
          </div>
          <button type="submit" style="color:green">Add Details</button>
          &nbsp;&nbsp;&nbsp;&nbsp;
          <a routerLink="/viewHotel">Cancel</a>
          <br />
        </form>
      </div>
      <div class="col-md-4">
      </div>
      <br />
    </div>
  </div>
