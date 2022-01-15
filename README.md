
# Em quên gửi file sql tạo database trong google form, em xin gửi code ở đây ạ
use master
create database HR
go
use HR
go
create table Employee_2119050079(
	IdEmployee varchar(50),
	Name nvarchar(50),
	DateBirth date,
	Gender bit,
	PlaceBirth nvarchar(50),
	IdDepartment varchar(50)
)
go
create table Department_2119050079 (
	IdDepartment varchar(50),
	Name nvarchar(50)
)
go

insert into Department_2119050079 values('IT', N'Công Nghệ Thông Tin')
insert into Department_2119050079 values('KT', N'Kế toán')
insert into Department_2119050079 values('KSNB', N'Kiểm Soát Nội Bộ')

go
insert into Employee_2119050079 values('IT001', N'Đoàn Nam Khôi', '11/07/2001', 1, N'Cà Mau', 'IT')
insert into Employee_2119050079 values('IT002', N'Nguyễn Tấn Phùng', '11/08/2001', 1, N'Khánh Hòa', 'IT')
insert into Employee_2119050079 values('IT003', N'Đào Anh Thư', '11/09/2001', 0, N'TP.HCM', 'IT')
insert into Employee_2119050079 values('IT004', N'Đỗ Thu Hà', '11/11/2001', 0, N'Hà Nội', 'IT')
insert into Employee_2119050079 values('IT005', N'Trần Tiến', '11/10/2001', 1, N'Lâm Đồng', 'IT')
insert into Employee_2119050079 values('IT006', N'Trần Tiến', '11/10/2001', 1, N'Hà Nội', 'IT')
insert into Employee_2119050079 values('IT007', N'Trần Tiến', '11/10/2001', 1, N'Đà Nẵng', 'IT')
insert into Employee_2119050079 values('IT008', N'Đào Ngọc Ánh', '11/10/2001', 0, N'Hà Nội', 'IT')

insert into Employee_2119050079 values('KT001', N'Trần Tiến Hoàng', '01/01/2001', 1, N'Hà Nội', 'KT')
insert into Employee_2119050079 values('KT002', N'Lý Huệ Trân', '11/02/2001', 0, N'Bắc Ninh', 'KT')
insert into Employee_2119050079 values('KT003', N'Trần Văn Khôi', '11/03/2001', 1, N'Bình Thuận', 'KT')
insert into Employee_2119050079 values('KT004', N'Đào Bích Hạnh', '11/04/2001', 0, N'Ninh Bình', 'KT')
insert into Employee_2119050079 values('KT005', N'Nguyễn An Bình', '11/05/2001', 1, N'HÀ Nam', 'KT')
insert into Employee_2119050079 values('KT006', N'Dương Hoàng Yến', '11/06/2001', 0, N'Đà Nẵng', 'KT')

insert into Employee_2119050079 values('KS001', N'Trần Tiến', '11/10/2001', 1, N'TP.HCM', 'KSNB')
insert into Employee_2119050079 values('KS002', N'Trần Tiến', '11/10/2001', 1, N'Hà Nội', 'KSNB')
insert into Employee_2119050079 values('KS003', N'Kim Oanh', '11/10/2001', 0, N'TP.HCM', 'KSNB')
insert into Employee_2119050079 values('KS004', N'Trần Tiến', '11/10/2001', 1, N'Hà Nội', 'KSNB')
insert into Employee_2119050079 values('KS005', N'Trần Tiến', '11/10/2001', 1, N'Hà Nội', 'KSNB')
insert into Employee_2119050079 values('KS006', N'Lê Minh Duy', '11/10/2001', 1, N'Hà Nội', 'KSNB')
insert into Employee_2119050079 values('KS007', N'Trần Tiến', '11/10/2000', 1, N'TP.HCM', 'KSNB')
insert into Employee_2119050079 values('KS008', N'Thúy Nga', '11/10/2000', 0, N'Hà Nội', 'KSNB')
insert into Employee_2119050079 values('KS009', N'Trần Tiến', '11/10/2000', 1, N'Cần Thơ', 'KSNB')
insert into Employee_2119050079 values('KS010', N'Trần Tiến', '11/10/2000', 1, N'Hà Nội', 'KSNB')
insert into Employee_2119050079 values('KS011', N'Lê Đình Nam', '11/10/2000', 1, N'TP.HCM', 'KSNB')

go

create proc spReadEmployee
as
begin
select * from Employee_2119050079
end

go

create proc spInsertEmployee
@IdEmployee varchar(50),
@Name nvarchar(50),
@DateBirth date,
@Gender bit,
@PlaceBirth nvarchar(50),
@IdDepartment varchar(50)
as
begin
    insert Employee_2119050079(IdEmployee, Name, DateBirth, Gender, PlaceBirth, IdDepartment) values(@IdEmployee, @Name, @DateBirth, @Gender, @PlaceBirth, @IdDepartment)
end

go

create proc spUpdateEmployee
@IdEmployee varchar(50),
@Name nvarchar(50),
@DateBirth date,
@Gender bit,
@PlaceBirth nvarchar(50),
@IdDepartment varchar(50)
as
begin
    update Employee_2119050079
    set
        Name = @Name,
        DateBirth =@DateBirth,
        Gender =@Gender,
		PlaceBirth=@PlaceBirth,
		IdDepartment=@IdDepartment
    where IdEmployee = @IdEmployee
end

go

create proc spDeleteEmployee
@IdEmployee varchar(50)
as
begin
    delete Employee_2119050079 where IdEmployee = @IdEmployee
end

go
