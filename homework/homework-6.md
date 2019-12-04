### mysql数据库作业
#### mysql作业题
```
-- 创建表和数据库
-- CREATE DATABASE yikongjian;
-- USE yikongjian;
CREATE TABLE student (
	Sno VARCHAR (20) NOT NULL,
	Sname VARCHAR (20) NOT NULL,
	Ssex VARCHAR (20) NOT NULL,
	Sbirthday datetime,
	Class VARCHAR (20),
	PRIMARY KEY (Sno)
) ENGINE = INNODB DEFAULT CHARSET = utf8;

CREATE TABLE Teacher (
	Tno VARCHAR (20) NOT NULL,
	Tname VARCHAR (20) NOT NULL,
	Tsex VARCHAR (20) NOT NULL,
	Tbirthday datetime,
	Prof VARCHAR (20),
	Depart VARCHAR (20) NOT NULL,
	PRIMARY KEY (Tno)
) ENGINE = INNODB DEFAULT CHARSET = utf8;

CREATE TABLE Course (
	Cno VARCHAR (20) NOT NULL,
	Cname VARCHAR (20) NOT NULL,
	Tno VARCHAR (20) NOT NULL,
	PRIMARY KEY (Cno),
	FOREIGN KEY (Tno) REFERENCES Teacher (Tno)
) ENGINE = INNODB DEFAULT CHARSET = utf8;

CREATE TABLE Score (
	Sno VARCHAR (20) NOT NULL,
	Cno VARCHAR (20) NOT NULL,
	Degree DECIMAL (4, 1),
	PRIMARY KEY (Sno, Cno),
	FOREIGN KEY (Sno) REFERENCES student (Sno),
	FOREIGN KEY (Cno) REFERENCES course (Cno)
) ENGINE = INNODB DEFAULT CHARSET = utf8;


INSERT INTO student (
	sno,
	sname,
	ssex,
	sbirthday,
	class
)
VALUES
	(
		108,
		'曾华',
		'男',
		'1977-09-01',
		95033
	);

INSERT INTO student (
	sno,
	sname,
	ssex,
	sbirthday,
	class
)
VALUES
	(
		105,
		'匡明',
		'男',
		'1975-10-02',
		95031
	);

INSERT INTO student (
	sno,
	sname,
	ssex,
	sbirthday,
	class
)
VALUES
	(
		107,
		'王丽',
		'女',
		'1976-01-23',
		95033
	);

INSERT INTO student (
	sno,
	sname,
	ssex,
	sbirthday,
	class
)
VALUES
	(
		101,
		'李军',
		'男',
		'1976-02-20',
		95033
	);

INSERT INTO student (
	sno,
	sname,
	ssex,
	sbirthday,
	class
)
VALUES
	(
		109,
		'王芳',
		'女',
		'1975-02-10',
		95031
	);

INSERT INTO student (
	sno,
	sname,
	ssex,
	sbirthday,
	class
)
VALUES
	(
		103,
		'陆君',
		'男',
		'1974-06-03',
		95031
	);

INSERT INTO teacher (
	tno,
	tname,
	tsex,
	tbirthday,
	prof,
	depart
)
VALUES
	(
		804,
		'李诚',
		'男',
		'1958-12-02',
		'副教授',
		'计算机系'
	);

INSERT INTO teacher (
	tno,
	tname,
	tsex,
	tbirthday,
	prof,
	depart
)
VALUES
	(
		856,
		'张旭',
		'男',
		'1969-03-12',
		'讲师',
		'电子工程系'
	);

INSERT INTO teacher (
	tno,
	tname,
	tsex,
	tbirthday,
	prof,
	depart
)
VALUES
	(
		825,
		'王萍',
		'女',
		'1972-05-05',
		'助教',
		'计算机系'
	);

INSERT INTO teacher (
	tno,
	tname,
	tsex,
	tbirthday,
	prof,
	depart
)
VALUES
	(
		831,
		'刘冰',
		'女',
		'1977-08-14',
		'助教',
		'电子工程系'
	);

INSERT INTO course (cno, cname, tno)
VALUES
	(
		'3-105',
		'计算机导论',
		825
	);

INSERT INTO course (cno, cname, tno)
VALUES
	('3-245', '操作系统', 804);

INSERT INTO course (cno, cname, tno)
VALUES
	('6-166', '数字电路', 856);

INSERT INTO course (cno, cname, tno)
VALUES
	('9-888', '高等数学', 831);

INSERT INTO score (sno, cno, degree)
VALUES
	(103, '3-245', 86);

INSERT INTO score (sno, cno, degree)
VALUES
	(105, '3-245', 75);

INSERT INTO score (sno, cno, degree)
VALUES
	(109, '3-245', 68);

INSERT INTO score (sno, cno, degree)
VALUES
	(103, '3-105', 92);

INSERT INTO score (sno, cno, degree)
VALUES
	(105, '3-105', 88);

INSERT INTO score (sno, cno, degree)
VALUES
	(109, '3-105', 76);

INSERT INTO score (sno, cno, degree)
VALUES
	(101, '3-105', 64);

INSERT INTO score (sno, cno, degree)
VALUES
	(107, '3-105', 91);

INSERT INTO score (sno, cno, degree)
VALUES
	(108, '3-105', 78);

INSERT INTO score (sno, cno, degree)
VALUES
	(101, '6-166', 85);

INSERT INTO score (sno, cno, degree)
VALUES
	(107, '6-166', 79);

INSERT INTO score (sno, cno, degree)
VALUES
	(108, '6-166', 81);
```

```
-- 查询
-- 1. 查询student表中的所有记录sname、ssex和class列
SELECT sname,ssex,class FROM student;
-- 2. 查询教师所有的单位即不重复的depart列
SELECT depart FROM teacher GROUP BY Depart;
-- 3. 查询student表的所有记录
SELECT * FROM student;
-- 4. 查询score表中成绩在60到80之间的所有记录
SELECT * FROM score WHERE score.Degree >= 60 AND score.Degree <=80;
-- 5. 查询score表中成绩为85，86或88的记录
SELECT * FROM score WHERE score.Degree in (85,86,88);
-- 6. 查询student表中“95031”班或性别为“女”的同学记录
SELECT * FROM student WHERE student.Class = 95031 or Ssex LIKE '女';
-- 7. 以class降序查询student表的所有记录
SELECT * FROM student ORDER BY Class DESC;
-- 8. 以cno升序，degree降序查询score表的所有记录
SELECT * FROM score ORDER BY cno, Degree DESC;
-- 9. 查询“95031”班的学生人数
SELECT * FROM student WHERE Class = 95031;
-- 10. 查询score表中的最高分的学生学号和课程号（子查询或者排序）
SELECT * FROM score ORDER BY Degree DESC LIMIT 1;
-- 11. 查询每门课的平均成绩
SELECT cno,AVG(Degree)FROM score GROUP BY Cno;
-- 12. 查询score表中至少有5名学生选修的并以3开头的课程的平均分数
SELECT Cno as a, COUNT(Cno) as b FROM score GROUP BY Cno;  --查询每门课学习人数
SELECT AVG(degree) FROM score, (SELECT Cno as a, COUNT(Cno) as b FROM score GROUP BY Cno) as t WHERE cno LIKE '3%' AND cno = t.a AND t.b>=5
-- 13. 查询分数大于70，小于90的sno列 
SELECT Sno FROM score WHERE Degree BETWEEN 70 AND 90;
```