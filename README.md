import { Component, OnInit } from '@angular/core';
import { FormGroup, FormBuilder, Validators } from '@angular/forms';
import { TravelAwayService } from '../../services/travel-away.service';
import { Router } from '@angular/router';

@Component({
  selector: 'app-addvehicle',
  templateUrl: './addvehicle.component.html',
  styleUrls: ['./addvehicle.component.css']
})
export class AddvehicleComponent implements OnInit {
  VehicleForm: FormGroup
  status: boolean;
  errorAddMsg: string;
  showDiv: boolean = false;
  msg: string;
  constructor(private _formBuilder: FormBuilder, private service: TravelAwayService, private _router: Router) { }

  ngOnInit(): void {
    var vnamePattern: string = "^[A-Za-z]*$";
    var rate = "^[1-9][0-9]*$";
    this.VehicleForm = this._formBuilder.group({
      VehicleName: ['', [Validators.required, Validators.pattern(vnamePattern)]],
      VehicleType: [''],
      RatePerHour: ['', [Validators.required, Validators.pattern(rate)]],
      RatePerKm: ['', [Validators.required, Validators.pattern(rate)]],
    }
    )
  }

  SubmitForm(form: FormGroup) {
    this.service.addVehicle(this.VehicleForm.value.VehicleName,
      this.VehicleForm.value.VehicleType, this.VehicleForm.value.RatePerHour, this.VehicleForm.value.RatePerKm).subscribe(
        resSuccess => {
          this.status = resSuccess;
          if (resSuccess) {
            alert('Vehicle added Successfully');
            this._router.navigate(['/viewVehicle'])
          }
          else {
            alert('Vehicle details could not be added')
          }
        },

        err => {
          this.errorAddMsg = err;
          alert( 'Sorry....Some error occurred,please try again');
        },
        () => console.log('Add Vehicle completed')
      )
  }

}
