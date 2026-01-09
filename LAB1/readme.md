
CREATE DATABASE PolyOE;
GO

USE PolyOE;
GO

CREATE TABLE dbo.Users (
Id NVARCHAR(20) NOT NULL PRIMARY KEY,
Password NVARCHAR(50) NOT NULL,
Fullname NVARCHAR(50) NOT NULL,
Email NVARCHAR(50) NOT NULL,
Admin BIT NOT NULL, 
);
GO


INSERT INTO dbo.Users(Id, Password, Fullname, Email, Admin) VALUES
('U01','123',N'Đậu văn phộng','a@fpt.edu.vn',0),
('U02','123',N'Bánh văn C','b@fpt.edu.vn',0),
('U03','123',N'Lý Thiên A','c@fpt.edu.vn',0),
('AD01','123',N'Admin1','admin@fpt.edu.vn',1);
GO

SELECT * FROM dbo.Users;
GO

USE PolyOE;
GO

DECLARE @i INT = 4;
WHILE @i <= 25
BEGIN
  INSERT INTO dbo.Users(Id, Password, Fullname, Email, Admin)
  VALUES (
    CONCAT('U', RIGHT('00' + CAST(@i AS VARCHAR(2)), 2)),
    '123',
    CONCAT(N'User ', @i),
    CONCAT('user', @i, '@fpt.edu.vn'),
    0
  );
  SET @i = @i + 1;
END
GO

SELECT COUNT(*) AS TotalUsers FROM dbo.Users;
GO
