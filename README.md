# use trains;
alter table schedule_stations rename column arival_time to arrival_time;
create table trains(
	id int,
    train_no int,
    primary key (id)	
);

create table train_schedules(
	id int,
    train_id int,
    operating_day varchar(100),
    schedule_id int,
    primary key (id),
    unique key(schedule_id),
    foreign key (train_id) references trains(id)
);

create table schedule_days(
	schedule_id int,
    date date,
    primary key(schedule_id),
    foreign key(schedule_id) references train_schedules(id)
);

create table schedule_stations(
	id int,
    station_id int,
    arival_time time,
    departure_time time,
    primary key(id),
    unique key(station_id),
    foreign key(id) references train_schedules(schedule_id)
);

create table stations(
	id int,
    station_name varchar(100),
    primary key(id),
    foreign key(id) references schedule_stations(station_id)
);


insert into trains(id, train_no) values('1','1234');
insert into trains(id, train_no) values('2','5678');
insert into trains(id, train_no) values('3','9101');
insert into trains(id, train_no) values('4','1213');

insert into train_schedules(id, train_id, operating_day, schedule_id) values('1','1','monday','21');
insert into train_schedules(id, train_id, operating_day, schedule_id) values('2','2','tuesday','22');
insert into train_schedules(id, train_id, operating_day, schedule_id) values('3','3','wednesday','23');
insert into train_schedules(id, train_id, operating_day, schedule_id) values('4','4','thursday','24');

insert into schedule_days(schedule_id, date) values('1','2022-09-19');
insert into schedule_days(schedule_id, date) values('2','2022-09-20');
insert into schedule_days(schedule_id, date) values('3','2022-09-21');
insert into schedule_days(schedule_id, date) values('4','2022-09-22');

insert into schedule_stations(id, station_id, arrival_time, departure_time) values('21','3132','06:06:00','07:00:00');
insert into schedule_stations(id, station_id, arrival_time, departure_time) values('22','3334','07:30:00','08:30:00');
insert into schedule_stations(id, station_id, arrival_time, departure_time) values('23','3536','08:30:00','09:30:00');
insert into schedule_stations(id, station_id, arrival_time, departure_time) values('24','3738','10:00:00','11:00:00');

insert into stations(id, station_name) values ('3132','mumbai');
insert into stations(id, station_name) values ('3334','pune');
insert into stations(id, station_name) values ('3536','nagpur');
insert into stations(id, station_name) values ('3738','delhi');



