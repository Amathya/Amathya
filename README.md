import { Component, OnInit } from '@angular/core';
import { FormGroup, FormBuilder, Validators } from '@angular/forms';
import { TravelAwayService } from '../../services/travel-away.service';
import { Router } from '@angular/router';

@Component({
  selector: 'app-addhotel',
  templateUrl: './addhotel.component.html',
  styleUrls: ['./addhotel.component.css']
})
export class AddhotelComponent implements OnInit {

  HotelForm: FormGroup
  status: boolean;
  errorAddMsg: string;
  showDiv: boolean = false;
  msg: string;
  constructor(private _formBuilder: FormBuilder, private service: TravelAwayService, private _router: Router) { }

  ngOnInit(): void {
    var citypattern: string = "^[A-Za-z]*$";
    var rate = "^[1-9][0-9]*$";
    this.HotelForm = this._formBuilder.group({
      HotelName: ['', [Validators.required, Validators.pattern(citypattern)]],
      HotelRating: [''],
      SingleRoomPrice: ['', [Validators.required, Validators.pattern(rate)]],
      DoubleRoomPrice: ['', [Validators.required, Validators.pattern(rate)]],
      DeluxeRoomPrice: ['', [Validators.required, Validators.pattern(rate)]],
      SuitePrice: ['', [Validators.required, Validators.pattern(rate)]],
      City: ['', [Validators.required, Validators.pattern(citypattern)]],
    }
    )
  }

  SubmitForm(form: FormGroup) {
    this.service.addHotel(this.HotelForm.value.HotelName,
      this.HotelForm.value.HotelRating, this.HotelForm.value.SingleRoomPrice,
      this.HotelForm.value.DoubleRoomPrice, this.HotelForm.value.DeluxeRoomPrice,
      this.HotelForm.value.SuitePrice, this.HotelForm.value.City).subscribe(
        resSuccess => {
          this.status = resSuccess;
          if (resSuccess) {
            alert('Hotel added Successfully');
            this._router.navigate(['/viewHotel'])
          }
          else
            alert("Sorry,Hotel details could not be added")

        },

        err => {
          this.errorAddMsg = err;
          alert('Sorry....Some error occurred,please try again');
        },
        () => console.log('Add Hotel completed')
      )
  }

}
