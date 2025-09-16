
Table Airport{
  airport_id integer  [primary key]
  airport_name varchar
  country varchar
  state varchar
  city varchar
  createdAT datetime
  UpdatedAT datetime
}

Table Flights_Information {
  flight_id integer  [pk]
  departing_gate varchar
  arriving_gate varchar
  createdAT datetime
  UpdatedAT datetime
  Airline_id integer
  departure_airportid integer
  arrival_airportid integer 
  scheduled_deperturetime datetime
  scheduled_arrivaltime datetime
  actual_deperturetime datetime
  actual_arrivaltime datetime
}

Table Airlines{
  airline_id int [pk]
  airline_code varchar
  airline_name varchar
  country varchar
  createdAT datetime
  UpdatedAT datetime
}

Table Bookings {
  booking_id int [pk]
  flight_id int 
  status varchar
  booking_platform varchar 
  createdAT datetime
  UpdatedAT datetime
  ticket_price int
  passenger_id int
}

Table Boarding_pass {
  boarding_pass_id int [pk]
  seat varchar 
  boarding_time datetime
  createdAT datetime
  UpdatedAT datetime 
  booking int 
}

Table Security_check {
  Security_check_id int [pk]
  cheach_results varchar
  createdAT datetime
  UpdatedAT datetime
  pessenger_id int
}

Table Passenger_information {
  pessenger_id int [pk]
  First_name varchar
  last_name varchar
  gender varchar 
  date_of_birth date
  county_of_citizenship varchar
  country_of_residence varchar
  passport_number varchar
  createdAT datetime
  UpdatedAT datetime
}

Table check {
  checking_id int [pk]
  check_results varchar 
  createdAT datetime
  UpdatedAT datetime
  booking_id int [pk]
  pessenger_id int 
}

Table Baggage {
  baggage_id int [pk]
  weight int
  createdAT datetime
  UpdatedAT datetime
  booking_id int [pk]
}

Table booking_change {
  change_id int [pk]
  booking_id int [pk]
  ChangeAt datetime
  change_description varchar
}


Ref: Flights_Information.flight_id > Airport.airport_id
Ref: Flights_Information.flight_id > Airlines.airline_id
Ref: Airlines.airline_id > Bookings.booking_id
Ref: Bookings.booking_id > Flights_Information.flight_id
Ref: Bookings.booking_id > Passenger_information.pessenger_id
Ref: Boarding_pass.boarding_pass_id > Bookings.booking_id
Ref: booking_change.change_id > Bookings.booking_id
Ref: Baggage.baggage_id > Bookings.booking_id
Ref: Security_check.Security_check_id < Passenger_information.pessenger_id
Ref: Passenger_information.pessenger_id < check.checking_id
Ref: check.checking_id > Baggage.baggage_id




