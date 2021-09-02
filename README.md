<app-employeelayout>
</app-employeelayout>
<div style="background-color:cornsilk" class="container">
  <h1 style="text-align:center">Add Vehicle</h1>
  <div style="text-align:center;margin-left:20em">
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; *All fileds are manadatory
  </div>

  <div class="row">
    <div class="col-md-4">
    </div>
    <div class="col-md-4">
      <form [formGroup]="VehicleForm" (ngSubmit)="SubmitForm(VehicleForm)">
        <div class="form-group">
          <label>Vehicle Name</label>
          <input type="text" class="form-control" placeholder="Enter the Vehicle name" formControlName="VehicleName">
          <p *ngIf="VehicleForm.controls.VehicleName.errors?.required &&  VehicleForm.controls.VehicleName.touched"
             style="color:red" class="alert alert-danger">&nbsp;This field is required!</p>
          <p *ngIf="VehicleForm.controls.VehicleName.errors?.pattern && VehicleForm.controls.VehicleName.touched "
             style="color:red" class="alert alert-danger">Only Alphabets are allowed!</p>
        </div>
        <div class="form-group">
          <label>Vehicle Type</label>
          <select class="form-control" placeholder="--Vehicle Type--" formControlName="VehicleType">
            <option value="Two-Wheeler">Two-Wheeler</option>
            <option value="Four-Wheeler">Four-Wheeler</option>
            <option value="Mini-Bus">Mini-Bus</option>
          </select>
        </div>
        <div class="form-group">
          <label>Rate Per Hour</label>
          <input type="number" class="form-control" placeholder="Enter the rate per hour" formControlName="RatePerHour">
          <p *ngIf="VehicleForm.controls.RatePerHour.errors?.required &&  VehicleForm.controls.RatePerHour.touched"
             class="alert alert-danger" style="color:red">This field is required!</p>
          <p *ngIf="VehicleForm.controls.RatePerHour.errors?.pattern  && VehicleForm.controls.RatePerHour.touched"
             style="color:red" class="alert alert-danger">only numbers are allowed!</p>
        </div>
        <div class="form-group">
          <label>Rate Per Km</label>
          <input type="number" class="form-control" placeholder="Enter the rate per Kilo-meter" formControlName="RatePerKm">
          <p *ngIf="VehicleForm.controls.RatePerKm.errors?.required &&  VehicleForm.controls.RatePerKm.touched"
             class="alert alert-danger" style="color:red">This field is required!</p>
          <p *ngIf="VehicleForm.controls.RatePerKm.errors?.pattern && VehicleForm.controls.RatePerKm.touched"
             style="color:red" class="alert alert-danger">only numbers are allowed!</p>
        </div>
        <button type="submit" style="color:green">Add Details</button>&nbsp;&nbsp;&nbsp;&nbsp;
        <a routerLink="/viewVehicle">Cancel</a>
        <br />
      </form>
    </div>
    <div class="col-md-4">
    </div>
    <br />
  </div>
</div>
