"# Angular 5 Geolocation Service" 

How to called in component.
Add the reference in component class file.
1) import { GeoLocationService } from './geo-location.service';
2) ChangeDetectorRef from @angular/core
    import { Component, OnInit, ChangeDetectorRef } from '@angular/core';
3) Add fllowing line in constructor
errorMsg: string;
currentLocation: Coordinates = null;
constructor(
    private ref: ChangeDetectorRef,   
    private geoLocationService: GeoLocationService
  ) { }
4) Call service 
searchByCurrent() {
    let self = this;    
    const accuracy = { enableHighAccuracy: true };
    self.geoLocationService.getLocation(accuracy).subscribe(
      function(position) {             
        self.currentLocation = position;
        self.ref.detectChanges();  
      },
      function(error) {
        self.errorMsg = error;
        self.ref.detectChanges();
      }
  );
