USE LibraryDB;
SELECT COUNT(*) AS TotalBooks
FROM Books;
SELECT Genre, COUNT(*) AS TotalBooks
FROM Books
GROUP BY Genre;
SELECT A.Name AS AuthorName, AVG(B.PublishedYear) AS AvgYear
FROM Books B
JOIN Authors A ON B.AuthorID = A.AuthorID
GROUP BY A.Name;
SELECT YEAR(MembershipDate) AS JoinYear, COUNT(*) AS TotalMembers
FROM Members
GROUP BY YEAR(MembershipDate);
SELECT A.Name AS AuthorName, COUNT(*) AS BookCount
FROM Books B
JOIN Authors A ON B.AuthorID = A.AuthorID
GROUP BY A.Name
HAVING COUNT(*) > 1;
SELECT AVG(DATEDIFF(ReturnDate, BorrowDate)) AS AvgBorrowDays
FROM Borrow
WHERE ReturnDate IS NOT NULL;
SELECT M.Name AS MemberName, COUNT(*) AS BorrowCount
FROM Borrow BR
JOIN Members M ON BR.MemberID = M.MemberID
GROUP BY M.Name;
SELECT A.Name AS AuthorName, COUNT(*) AS TotalBorrowed
FROM Borrow BR
JOIN Books B ON BR.BookID = B.BookID
JOIN Authors A ON B.AuthorID = A.AuthorID
GROUP BY A.Name;
SELECT ROUND(AVG(PublishedYear), 0) AS RoundedAvgYear
FROM Books;
SELECT COUNT(DISTINCT Genre) AS UniqueGenres
FROM Books;
