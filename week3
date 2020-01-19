
--Creation of Tables
CREATE TABLE Users (
	userID int NOT NULL AUTO_INCREMENT,
	name VARCHAR(255) NOT NULL,
	groupID int,
	PRIMARY KEY (userID)
);

CREATE TABLE Groups (
	groupID int NOT NULL AUTO_INCREMENT,
	groupName VARCHAR(50),
	PRIMARY KEY (groupID)
);

CREATE TABLE Rooms (
	roomID int NOT NULL AUTO_INCREMENT,
	roomName VARCHAR(50),
	PRIMARY KEY (roomID)
);

CREATE TABLE Permissions (
	groupID int NOT NULL,
	roomID int NOT NULL,
	FOREIGN KEY (groupID) REFERENCES Groups(groupID),
	FOREIGN KEY (roomID) REFERENCES Rooms(roomID)
);

--Insertion of Values

INSERT INTO Groups (groupName)
VALUES 
	('I.T'),
	('Sales'),
	('Administration'),
	('Operations');

INSERT INTO Rooms (roomName)
VALUES
	('101'),
	('102'),
	('Auditorium A'),
	('Auditorium B');

INSERT INTO Users (name, groupID)
VALUES
	('Modesto', 1),
	('Ayine', 1),
	('Christopher', 2),
	('Cheong woo', 2),
	('Saulat', 3),
	('Heidy', NULL);

INSERT INTO Permissions (groupID, roomID)
VALUES (1,1), (1,2), (2,2), (2,3);

--SELECT Statements
--All groups, and the users in each group. A group should appear even if there are no users assigned to the group.

SELECT A.groupName, B.name 
FROM Users B RIGHT JOIN Groups A
ON B.groupID = A.groupID;



--All rooms, and the groups assigned to each room. The rooms should appear even if no groups have been assigned to them.

SELECT R.roomName, G.groupName
FROM Permissions P
	RIGHT JOIN Rooms R ON R.roomID = P.roomID
	LEFT JOIN Groups G ON G.groupID = P.groupID;


--A list of users, the groups that they belong to, and the rooms to which they are assigned. This should be sorted alphabetically by user, then by group, then by room.

SELECT U.name, G.groupName, R.roomName
FROM Users U 
	INNER JOIN Groups G ON U.groupID = G.groupID
	RIGHT JOIN Permissions P ON P.groupID = G.groupID
	RIGHT JOIN Rooms R ON R.roomID = P.roomID
ORDER BY U.name, G.groupName, R.roomName
