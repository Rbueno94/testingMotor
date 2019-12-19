USE [reingenieria]
GO
/****** Object:  UserDefinedFunction [dbo].[listarasignaciones]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       FUNCTION [dbo].[listarasignaciones](@asigcab integer)
RETURNS @query TABLE (
	 id int,
	lunEnt time,
	lunSal time,
	marEnt time,
	marSal time,
	mieEnt time,
	mieSal time,
	jueEnt time,
	jueSal time,
	vieEnt time,
	vieSal time,
	sabEnt time,
	sabSal time,
	domEnt time,
	domSal time,
	asignacionCab_id int ,
	operario_id int ,
	fechaInicio date,
	totalHoras nvarchar(8) ,
	numTotalHoras int ,
	fechaFin date,
	supervisor bit ,
	perfil_id int,
	eliminado bit ,
	tipo nvarchar(12)
)
BEGIN
	insert @query
	SELECT [id],[lunEnt],[lunSal],[marEnt],[marSal],[mieEnt],[mieSal],[jueEnt],[jueSal],[vieEnt],[vieSal],[sabEnt],[sabSal],[domEnt],[domSal],
	[asignacionCab_id],[operario_id],[fechaInicio],[totalHoras],numTotalHoras,[fechaFin],[supervisor],[perfil_id],[eliminado],'persistido'
	FROM [dbo].[Operarios_asignaciondet] where asignacionCab_id=@asigcab
	union 
	SELECT [id],[lunEnt],[lunSal],[marEnt],[marSal],[mieEnt],[mieSal],[jueEnt],[jueSal],[vieEnt],[vieSal],[sabEnt],[sabSal],[domEnt],[domSal],
	[asignacionCab_id],[operario_id],[fechaInicio],[totalHoras],numTotalHoras,[fechaFin],[supervisor],[perfil_id],[eliminado],'temporal'
	FROM [dbo].[Operarios_asignaciondettemp] where  asignacionCab_id=@asigcab
	RETURN
END
GO
/****** Object:  Table [dbo].[Operarios_asignaciondettemp]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_asignaciondettemp](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[lunEnt] [time](7) NULL,
	[lunSal] [time](7) NULL,
	[marEnt] [time](7) NULL,
	[marSal] [time](7) NULL,
	[mieEnt] [time](7) NULL,
	[mieSal] [time](7) NULL,
	[jueEnt] [time](7) NULL,
	[jueSal] [time](7) NULL,
	[vieEnt] [time](7) NULL,
	[vieSal] [time](7) NULL,
	[sabEnt] [time](7) NULL,
	[sabSal] [time](7) NULL,
	[domEnt] [time](7) NULL,
	[domSal] [time](7) NULL,
	[fechaInicio] [date] NULL,
	[fechaFin] [date] NULL,
	[totalHoras] [nvarchar](8) NULL,
	[supervisor] [bit] NOT NULL,
	[eliminado] [bit] NOT NULL,
	[fechaCreacion] [datetime2](7) NOT NULL,
	[asignacionCab_id] [int] NULL,
	[operario_id] [int] NULL,
	[perfil_id] [int] NULL,
	[asignacionDet_original_id] [int] NULL,
	[remplazosCab_id] [int] NULL,
	[numTotalHoras] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_operario_profesion]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_operario_profesion](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[operario_id] [int] NOT NULL,
	[especializacion_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
 CONSTRAINT [Operarios_operario_profesion_operario_id_especializacion_id_af7e5172_uniq] UNIQUE NONCLUSTERED 
(
	[operario_id] ASC,
	[especializacion_id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_asignacioncab]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_asignacioncab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaUltimaMod] [datetime2](7) NOT NULL,
	[totalasignado] [nvarchar](8) NULL,
	[puntoServicio_id] [int] NULL,
	[usuario_id] [int] NULL,
	[reAsignar] [bit] NOT NULL,
	[numTotalAsignado] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_asignaciondet]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_asignaciondet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[lunEnt] [time](7) NULL,
	[lunSal] [time](7) NULL,
	[marEnt] [time](7) NULL,
	[marSal] [time](7) NULL,
	[mieEnt] [time](7) NULL,
	[mieSal] [time](7) NULL,
	[jueEnt] [time](7) NULL,
	[jueSal] [time](7) NULL,
	[vieEnt] [time](7) NULL,
	[vieSal] [time](7) NULL,
	[sabEnt] [time](7) NULL,
	[sabSal] [time](7) NULL,
	[domEnt] [time](7) NULL,
	[domSal] [time](7) NULL,
	[asignacionCab_id] [int] NULL,
	[operario_id] [int] NULL,
	[fechaInicio] [date] NULL,
	[totalHoras] [nvarchar](8) NULL,
	[fechaFin] [date] NULL,
	[supervisor] [bit] NOT NULL,
	[perfil_id] [int] NULL,
	[eliminado] [bit] NOT NULL,
	[numTotalHoras] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_especializacion]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_especializacion](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[especializacion] [nvarchar](200) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_operario]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_operario](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[nombre] [nvarchar](70) NOT NULL,
	[direccion] [nvarchar](100) NOT NULL,
	[barrios] [nvarchar](70) NOT NULL,
	[nroLegajo] [nvarchar](6) NOT NULL,
	[telefono] [bigint] NOT NULL,
	[fechaNacimiento] [date] NOT NULL,
	[lugarNacimiento_id] [nvarchar](30) NOT NULL,
	[numCedula] [nvarchar](30) NOT NULL,
	[numPasaporte] [nvarchar](10) NOT NULL,
	[email] [nvarchar](60) NOT NULL,
	[nombreContacto] [nvarchar](70) NOT NULL,
	[fechaInicio] [date] NOT NULL,
	[ciudad_id] [int] NOT NULL,
	[nacionalidad_id] [int] NOT NULL,
	[escolaridad] [nvarchar](70) NOT NULL,
	[banco] [nvarchar](30) NULL,
	[apellido] [nvarchar](70) NOT NULL,
	[telefonoContacto] [bigint] NULL,
	[fechaFin] [date] NULL,
	[ctaBanco] [nvarchar](20) NOT NULL,
	[longitud] [nvarchar](20) NOT NULL,
	[latitud] [nvarchar](20) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_puntoservicio]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_puntoservicio](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[CodPuntoServicio] [nvarchar](50) NOT NULL,
	[NombrePServicio] [nvarchar](100) NOT NULL,
	[DireccionContrato] [nvarchar](150) NOT NULL,
	[Barrios] [nvarchar](70) NOT NULL,
	[Contacto] [nvarchar](100) NOT NULL,
	[MailContacto] [nvarchar](70) NOT NULL,
	[TelefonoContacto] [nvarchar](100) NOT NULL,
	[Coordenadas] [nvarchar](100) NOT NULL,
	[Ciudad_id] [int] NOT NULL,
	[Cliente_id] [int] NOT NULL,
	[NumeroMarcador] [nvarchar](15) NULL,
	[activo] [bit] NOT NULL,
	[comentario] [nvarchar](200) NOT NULL,
	[usuario_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  View [dbo].[detalle_lista_operarios3_anterior]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE       VIEW [dbo].[detalle_lista_operarios3_anterior]
AS
SELECT        id_operario, nombres, nroLegajo, nombres_puntoServicio, ids_puntoServicio, totalHoras,
                             (SELECT DISTINCT STRING_AGG(esp.especializacion, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf LEFT OUTER JOIN
                                                         dbo.Operarios_especializacion AS esp ON esp.id = opf.especializacion_id
                               WHERE        (opf.operario_id = op_1.id_operario)) AS perfil, antiguedad,
                             (SELECT DISTINCT STRING_AGG(especializacion_id, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf
                               WHERE        (operario_id = op_1.id_operario)) AS ids_perfil
FROM            (SELECT        op.id AS id_operario, { fn CONCAT({ fn CONCAT(op.nombre, ' ') }, op.apellido) } AS nombres, op.nroLegajo, ISNULL(STRING_AGG(ps.NombrePServicio, ', '), '') AS nombres_puntoServicio, ISNULL(STRING_AGG(ps.id, 
                                                    ', '), ' ') AS ids_puntoServicio, SUM(CAST(ISNULL(aod.totalHoras, 0) AS float))+SUM(CAST(ISNULL(aodt.totalHoras, 0) AS float)) AS totalHoras, DATEDIFF(year, op.fechaInicio, GETDATE()) AS antiguedad
                          FROM            dbo.Operarios_operario AS op LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondet AS aod ON op.id = aod.operario_id LEFT OUTER JOIN
													dbo.Operarios_asignaciondettemp AS aodt ON op.id = aodt.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_asignacioncab AS aoc ON aod.asignacionCab_id = aoc.id OR aodt.asignacionCab_id = aoc.id LEFT OUTER JOIN
                                                    dbo.Operarios_puntoservicio AS ps ON ps.id = aoc.puntoServicio_id
                          GROUP BY op.id, op.nombre, op.apellido, op.nroLegajo, op.fechaInicio) AS op_1
GO
/****** Object:  View [dbo].[detalle_lista_operarios2]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE     VIEW [dbo].[detalle_lista_operarios2]
AS
SELECT        id_operario, nombres, nroLegajo, nombres_puntoServicio, ids_puntoServicio, totalHoras,
                             (SELECT DISTINCT STRING_AGG(esp.especializacion, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf LEFT OUTER JOIN
                                                         dbo.Operarios_especializacion AS esp ON esp.id = opf.especializacion_id
                               WHERE        (opf.operario_id = op_1.id_operario)) AS perfil, antiguedad,
                             (SELECT DISTINCT STRING_AGG(especializacion_id, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf
                               WHERE        (operario_id = op_1.id_operario)) AS ids_perfil
FROM            (SELECT        op.id AS id_operario, { fn CONCAT({ fn CONCAT(op.nombre, ' ') }, op.apellido) } AS nombres, op.nroLegajo, STRING_AGG(ps.NombrePServicio, ', ') AS nombres_puntoServicio, STRING_AGG(ps.id, ', ') 
                                                    AS ids_puntoServicio, SUM(CAST(ISNULL(aod.totalHoras, 0) AS float)) AS totalHoras, DATEDIFF(year, op.fechaInicio, GETDATE()) AS antiguedad
                          FROM            dbo.Operarios_operario AS op LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondet AS aod ON op.id = aod.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_asignacioncab AS aoc ON aod.asignacionCab_id = aoc.id LEFT OUTER JOIN
                                                    dbo.Operarios_puntoservicio AS ps ON ps.id = aoc.puntoServicio_id
                          GROUP BY op.id, op.nombre, op.apellido, op.nroLegajo, op.fechaInicio) AS op_1
GO
/****** Object:  Table [dbo].[Operarios_ciudad]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_ciudad](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[NombreCiudad] [nvarchar](70) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  View [dbo].[detalle_lista_operarios3]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE     VIEW [dbo].[detalle_lista_operarios3]
AS
SELECT        id_operario, nombres, nroLegajo, nombres_puntoServicio, ids_puntoServicio, totalHoras,
                             (SELECT DISTINCT STRING_AGG(esp.especializacion, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf LEFT OUTER JOIN
                                                         dbo.Operarios_especializacion AS esp ON esp.id = opf.especializacion_id
                               WHERE        (opf.operario_id = op_1.id_operario)) AS perfil, antiguedad,
                             (SELECT DISTINCT STRING_AGG(especializacion_id, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf
                               WHERE        (operario_id = op_1.id_operario)) AS ids_perfil,
                             (SELECT        NombreCiudad
                               FROM            dbo.Operarios_ciudad AS ct
                               WHERE        (id = op_1.ciudad)) AS ciudad
FROM            (SELECT        op.id AS id_operario, op.ciudad_id AS ciudad, { fn CONCAT({ fn CONCAT(op.nombre, ' ') }, op.apellido) } AS nombres, op.nroLegajo, ISNULL(STRING_AGG(ps.NombrePServicio, ', '), '') AS nombres_puntoServicio, 
                                                    ISNULL(STRING_AGG(ps.id, ', '), ' ') AS ids_puntoServicio, SUM(CAST(ISNULL(aod.totalHoras, 0) AS float)) + SUM(CAST(ISNULL(aodt.totalHoras, 0) AS float)) AS totalHoras, DATEDIFF(year, op.fechaInicio, GETDATE()) 
                                                    AS antiguedad
                          FROM            dbo.Operarios_operario AS op LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondet AS aod ON op.id = aod.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondettemp AS aodt ON op.id = aodt.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_asignacioncab AS aoc ON aod.asignacionCab_id = aoc.id OR aodt.asignacionCab_id = aoc.id LEFT OUTER JOIN
                                                    dbo.Operarios_puntoservicio AS ps ON ps.id = aoc.puntoServicio_id LEFT OUTER JOIN
                                                    dbo.Operarios_ciudad AS cd ON cd.id = op.ciudad_id
                          GROUP BY op.id, op.nombre, op.apellido, op.nroLegajo, op.fechaInicio, op.ciudad_id) AS op_1
GO
/****** Object:  View [dbo].[detalle_lista_operarios4]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE      VIEW [dbo].[detalle_lista_operarios4]
AS
SELECT        id_operario, nombres, nroLegajo, nombres_puntoServicio, ids_puntoServicio, totalHoras,
                             (SELECT DISTINCT STRING_AGG(esp.especializacion, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf LEFT OUTER JOIN
                                                         dbo.Operarios_especializacion AS esp ON esp.id = opf.especializacion_id
                               WHERE        (opf.operario_id = op_1.id_operario)) AS perfil, antiguedad,
                             (SELECT DISTINCT STRING_AGG(especializacion_id, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf
                               WHERE        (operario_id = op_1.id_operario)) AS ids_perfil,
                             (SELECT        NombreCiudad
                               FROM            dbo.Operarios_ciudad AS ct
                               WHERE        (id = op_1.ciudad)) AS ciudad
FROM            (SELECT        op.id AS id_operario, op.ciudad_id AS ciudad, { fn CONCAT({ fn CONCAT(op.nombre, ' ') }, op.apellido) } AS nombres, op.nroLegajo, ISNULL(STRING_AGG(ps.NombrePServicio, ', '), '') AS nombres_puntoServicio, 
                                                    ISNULL(STRING_AGG(ps.id, ', '), ' ') AS ids_puntoServicio, /*SUM(CAST(ISNULL(aod.totalHoras, 0) AS float)) + SUM(CAST(ISNULL(aodt.totalHoras, 0) AS float))*/0 AS totalHoras, DATEDIFF(year, op.fechaInicio, GETDATE()) 
                                                    AS antiguedad
                          FROM            dbo.Operarios_operario AS op LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondet AS aod ON op.id = aod.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondettemp AS aodt ON op.id = aodt.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_asignacioncab AS aoc ON aod.asignacionCab_id = aoc.id OR aodt.asignacionCab_id = aoc.id LEFT OUTER JOIN
                                                    dbo.Operarios_puntoservicio AS ps ON ps.id = aoc.puntoServicio_id LEFT OUTER JOIN
                                                    dbo.Operarios_ciudad AS cd ON cd.id = op.ciudad_id
                          GROUP BY op.id, op.nombre, op.apellido, op.nroLegajo, op.fechaInicio, op.ciudad_id) AS op_1
GO
/****** Object:  View [dbo].[detalle_lista_operarios]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE     VIEW [dbo].[detalle_lista_operarios]
AS
SELECT        id_operario, nombres, nroLegajo, nombres_puntoServicio, ids_puntoServicio, totalHoras,
                             (SELECT DISTINCT STRING_AGG(esp.especializacion, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf LEFT OUTER JOIN
                                                         dbo.Operarios_especializacion AS esp ON esp.id = opf.especializacion_id
                               WHERE        (opf.operario_id = op_1.id_operario)) AS perfil, antiguedad,
                             (SELECT DISTINCT STRING_AGG(especializacion_id, ', ') AS Expr1
                               FROM            dbo.Operarios_operario_profesion AS opf
                               WHERE        (operario_id = op_1.id_operario)) AS ids_perfil
FROM            (SELECT        op.id AS id_operario, { fn CONCAT({ fn CONCAT(op.nombre, ' ') }, op.apellido) } AS nombres, op.nroLegajo, ISNULL(STRING_AGG(ps.NombrePServicio, ', '), '') AS nombres_puntoServicio, ISNULL(STRING_AGG(ps.id, 
                                                    ', '), ' ') AS ids_puntoServicio, SUM(CAST(ISNULL(aod.totalHoras, 0) AS float)) AS totalHoras, DATEDIFF(year, op.fechaInicio, GETDATE()) AS antiguedad
                          FROM            dbo.Operarios_operario AS op LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondet AS aod ON op.id = aod.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_asignacioncab AS aoc ON aod.asignacionCab_id = aoc.id LEFT OUTER JOIN
                                                    dbo.Operarios_puntoservicio AS ps ON ps.id = aoc.puntoServicio_id
                          GROUP BY op.id, op.nombre, op.apellido, op.nroLegajo, op.fechaInicio) AS op_1
GO
/****** Object:  Table [dbo].[auth_group]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[auth_group](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[name] [nvarchar](80) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
UNIQUE NONCLUSTERED 
(
	[name] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[auth_group_permissions]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[auth_group_permissions](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[group_id] [int] NOT NULL,
	[permission_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
 CONSTRAINT [auth_group_permissions_group_id_permission_id_0cd325b0_uniq] UNIQUE NONCLUSTERED 
(
	[group_id] ASC,
	[permission_id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[auth_permission]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[auth_permission](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[name] [nvarchar](255) NOT NULL,
	[content_type_id] [int] NOT NULL,
	[codename] [nvarchar](100) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
 CONSTRAINT [auth_permission_content_type_id_codename_01ab375a_uniq] UNIQUE NONCLUSTERED 
(
	[content_type_id] ASC,
	[codename] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[auth_user]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[auth_user](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[password] [nvarchar](128) NOT NULL,
	[last_login] [datetime2](7) NULL,
	[is_superuser] [bit] NOT NULL,
	[username] [nvarchar](150) NOT NULL,
	[first_name] [nvarchar](30) NOT NULL,
	[last_name] [nvarchar](150) NOT NULL,
	[email] [nvarchar](254) NOT NULL,
	[is_staff] [bit] NOT NULL,
	[is_active] [bit] NOT NULL,
	[date_joined] [datetime2](7) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
 CONSTRAINT [auth_user_username_6821ab7c_uniq] UNIQUE NONCLUSTERED 
(
	[username] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[auth_user_groups]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[auth_user_groups](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[user_id] [int] NOT NULL,
	[group_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
 CONSTRAINT [auth_user_groups_user_id_group_id_94350c0c_uniq] UNIQUE NONCLUSTERED 
(
	[user_id] ASC,
	[group_id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[auth_user_user_permissions]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[auth_user_user_permissions](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[user_id] [int] NOT NULL,
	[permission_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
 CONSTRAINT [auth_user_user_permissions_user_id_permission_id_14a6b632_uniq] UNIQUE NONCLUSTERED 
(
	[user_id] ASC,
	[permission_id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[django_admin_log]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[django_admin_log](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[action_time] [datetime2](7) NOT NULL,
	[object_id] [nvarchar](max) NULL,
	[object_repr] [nvarchar](200) NOT NULL,
	[action_flag] [smallint] NOT NULL,
	[change_message] [nvarchar](max) NOT NULL,
	[content_type_id] [int] NULL,
	[user_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[django_content_type]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[django_content_type](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[app_label] [nvarchar](100) NOT NULL,
	[model] [nvarchar](100) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
 CONSTRAINT [django_content_type_app_label_model_76bd3d3b_uniq] UNIQUE NONCLUSTERED 
(
	[app_label] ASC,
	[model] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[django_migrations]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[django_migrations](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[app] [nvarchar](255) NOT NULL,
	[name] [nvarchar](255) NOT NULL,
	[applied] [datetime2](7) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[django_session]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[django_session](
	[session_key] [nvarchar](40) NOT NULL,
	[session_data] [nvarchar](max) NOT NULL,
	[expire_date] [datetime2](7) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[session_key] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ESME_EM_Marcaciones]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ESME_EM_Marcaciones](
	[IdPersonaEvento] [numeric](18, 0) IDENTITY(1,1) NOT NULL,
	[CodOperacion] [varchar](2) NULL,
	[CodPersona] [varchar](10) NULL,
	[CodCategoria] [varchar](2) NULL,
	[NumLinea] [char](10) NULL,
	[CodUbicacion] [varchar](30) NULL,
	[Fecha] [smalldatetime] NULL,
	[Estado] [varchar](20) NULL
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[infolog]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[infolog](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[info] [nvarchar](max) NULL,
	[fechaHora] [datetime] NULL,
 CONSTRAINT [PK_infolog] PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_actividadcab]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_actividadcab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaUltimaMod] [datetime2](7) NOT NULL,
	[totalasignado] [nvarchar](8) NULL,
	[numTotalAsignado] [int] NULL,
	[reAsignar] [bit] NOT NULL,
	[planificacionEsp_id] [int] NULL,
	[usuario_id] [int] NULL,
	[area] [nvarchar](50) NULL,
	[sector] [nvarchar](max) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_actividaddet]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_actividaddet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[lunEnt] [time](7) NULL,
	[lunSal] [time](7) NULL,
	[marEnt] [time](7) NULL,
	[marSal] [time](7) NULL,
	[mieEnt] [time](7) NULL,
	[mieSal] [time](7) NULL,
	[jueEnt] [time](7) NULL,
	[jueSal] [time](7) NULL,
	[vieEnt] [time](7) NULL,
	[vieSal] [time](7) NULL,
	[sabEnt] [time](7) NULL,
	[sabSal] [time](7) NULL,
	[domEnt] [time](7) NULL,
	[domSal] [time](7) NULL,
	[fechaInicio] [date] NULL,
	[fechaFin] [date] NULL,
	[totalHoras] [nvarchar](8) NULL,
	[numTotalHoras] [int] NULL,
	[supervisor] [bit] NOT NULL,
	[eliminado] [bit] NOT NULL,
	[actividadCab_id] [int] NULL,
	[operario_id] [int] NULL,
	[perfil_id] [int] NULL,
	[area] [nvarchar](50) NULL,
	[sector] [nvarchar](max) NULL,
	[cantidad] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_alertaresp]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_alertaresp](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[accion] [nvarchar](30) NOT NULL,
	[hora] [time](7) NULL,
	[motivo_id] [int] NULL,
	[fechaRetorno] [date] NULL,
	[comentarios] [nvarchar](1000) NOT NULL,
	[escalado] [bit] NOT NULL,
	[id_alerta_id] [int] NOT NULL,
	[usuario_id] [int] NULL,
	[id_reemplazo_id] [int] NULL,
	[fecha_creacion] [datetime2](7) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_alertas]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_alertas](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[FechaHora] [datetime2](7) NOT NULL,
	[Estado] [nvarchar](15) NOT NULL,
	[Tipo] [nvarchar](10) NOT NULL,
	[Asignacion_id] [int] NULL,
	[Operario_id] [int] NOT NULL,
	[PuntoServicio_id] [int] NULL,
	[Nivel] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_asigfiscalpuntoservicio]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_asigfiscalpuntoservicio](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[puntoServicio_id] [int] NOT NULL,
	[userFiscal_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_asigjefefiscal]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_asigjefefiscal](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[userFiscal_id] [int] NOT NULL,
	[userJefe_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_asignacionesdet]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_asignacionesdet](
	[id_opeario] [int] NOT NULL,
	[lunEnt] [time](7) NOT NULL,
	[lunSal] [time](7) NOT NULL,
	[marEnt] [time](7) NOT NULL,
	[marSal] [time](7) NOT NULL,
	[mieEnt] [time](7) NOT NULL,
	[mieSal] [time](7) NOT NULL,
	[jueEnt] [time](7) NOT NULL,
	[jueSal] [time](7) NOT NULL,
	[vieEnt] [time](7) NOT NULL,
	[vieSal] [time](7) NOT NULL,
	[sabEnt] [time](7) NOT NULL,
	[sabSal] [time](7) NOT NULL,
	[domEnt] [time](7) NOT NULL,
	[domSal] [time](7) NOT NULL,
	[asignacionCab_id] [int] NOT NULL,
	[operario_id] [int] NOT NULL,
	[fechaInicio] [date] NOT NULL,
	[totalHoras] [nvarchar](8) NOT NULL,
	[fechaFin] [date] NOT NULL,
	[supervisor] [bit] NOT NULL,
	[perfil] [int] NOT NULL,
	[eliminado] [bit] NOT NULL,
	[tipo] [nvarchar](12) NOT NULL,
	[numTotalHoras] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id_opeario] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_asignacionesprocesadas]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_asignacionesprocesadas](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[NumCedulaOperario] [nvarchar](30) NOT NULL,
	[fecha] [date] NOT NULL,
	[asignacionDet_id] [int] NULL,
	[puntoServicio_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_calendariocupo]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_calendariocupo](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[anho] [int] NULL,
	[mes] [nvarchar](2) NOT NULL,
	[cantLunes] [int] NULL,
	[cantMartes] [int] NULL,
	[cantMiercoles] [int] NULL,
	[cantJueves] [int] NULL,
	[cantViernes] [int] NULL,
	[cantSabado] [int] NULL,
	[cantDomingo] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_cargo]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_cargo](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[cargo] [nvarchar](100) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_cargoasignado]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_cargoasignado](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[cargo_id] [int] NULL,
	[user_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
UNIQUE NONCLUSTERED 
(
	[user_id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_cliente]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_cliente](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[Cliente] [nvarchar](100) NOT NULL,
	[CodigoCliente] [nvarchar](15) NOT NULL,
	[Direccion] [nvarchar](150) NOT NULL,
	[GrupoEmpresarial_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_cuporeal]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_cuporeal](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[anho] [int] NULL,
	[mes] [nvarchar](2) NOT NULL,
	[cupoCalculado] [int] NULL,
	[puntoServicio_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_cupoutilizado]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_cupoutilizado](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[anho] [int] NULL,
	[mes] [nvarchar](2) NOT NULL,
	[cupoUtilizado] [int] NULL,
	[horasProcesadas_id] [int] NULL,
	[puntoServicio_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_dialibre]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_dialibre](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaCreacion] [datetime2](7) NOT NULL,
	[domEnt] [time](7) NULL,
	[domSal] [time](7) NULL,
	[id_operario_id] [int] NULL,
	[jueEnt] [time](7) NULL,
	[jueSal] [time](7) NULL,
	[lunEnt] [time](7) NULL,
	[lunSal] [time](7) NULL,
	[marEnt] [time](7) NULL,
	[marSal] [time](7) NULL,
	[mieEnt] [time](7) NULL,
	[mieSal] [time](7) NULL,
	[sabEnt] [time](7) NULL,
	[sabSal] [time](7) NULL,
	[vieEnt] [time](7) NULL,
	[vieSal] [time](7) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_feriados]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_feriados](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[anho] [int] NULL,
	[fecha] [date] NULL,
	[descripcion] [nvarchar](200) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_generadoralertas]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_generadoralertas](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaInicio] [datetime2](7) NULL,
	[fechaFin] [datetime2](7) NULL,
	[cantidad] [int] NULL,
	[terminado] [bit] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_grupoempresarial]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_grupoempresarial](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[GrupoEmpresarial] [nvarchar](100) NOT NULL,
	[CodigoGrupo] [nvarchar](15) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_hisasigfiscalpuntoservicio]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_hisasigfiscalpuntoservicio](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fecha_inicio] [date] NOT NULL,
	[fecha_fin] [date] NULL,
	[puntoServicio_id] [int] NOT NULL,
	[userFiscal_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
UNIQUE NONCLUSTERED 
(
	[puntoServicio_id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_hisasigjefefiscal]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_hisasigjefefiscal](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fecha_inicio] [date] NOT NULL,
	[fecha_fin] [date] NULL,
	[userFiscal_id] [int] NOT NULL,
	[userJefe_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY],
UNIQUE NONCLUSTERED 
(
	[userFiscal_id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histactividadcab]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histactividadcab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaUltimaMod] [datetime2](7) NOT NULL,
	[totalasignado] [nvarchar](8) NULL,
	[numTotalAsignado] [int] NULL,
	[reAsignar] [bit] NOT NULL,
	[sector] [nvarchar](max) NULL,
	[area] [nvarchar](50) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[planificacionEsp_id] [int] NULL,
	[usuario_id] [int] NULL,
	[vactual_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histactividaddet]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histactividaddet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[lunEnt] [time](7) NULL,
	[lunSal] [time](7) NULL,
	[marEnt] [time](7) NULL,
	[marSal] [time](7) NULL,
	[mieEnt] [time](7) NULL,
	[mieSal] [time](7) NULL,
	[jueEnt] [time](7) NULL,
	[jueSal] [time](7) NULL,
	[vieEnt] [time](7) NULL,
	[vieSal] [time](7) NULL,
	[sabEnt] [time](7) NULL,
	[sabSal] [time](7) NULL,
	[domEnt] [time](7) NULL,
	[domSal] [time](7) NULL,
	[fechaInicio] [date] NULL,
	[fechaFin] [date] NULL,
	[totalHoras] [nvarchar](8) NULL,
	[numTotalHoras] [int] NULL,
	[supervisor] [bit] NOT NULL,
	[eliminado] [bit] NOT NULL,
	[sector] [nvarchar](max) NULL,
	[area] [nvarchar](50) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[actividadCab_id] [int] NULL,
	[operario_id] [int] NULL,
	[perfil_id] [int] NULL,
	[vactual_id] [int] NULL,
	[cantidad] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histasigfiscalpuntoservicio]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histasigfiscalpuntoservicio](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[vactual_id] [int] NULL,
	[puntoServicio_id] [int] NULL,
	[userFiscal_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histasigjefefiscal]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histasigjefefiscal](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[vactual_id] [int] NULL,
	[userFiscal_id] [int] NULL,
	[userJefe_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histasignacioncab]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histasignacioncab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaUltimaMod] [datetime2](7) NOT NULL,
	[totalasignado] [nvarchar](8) NULL,
	[reAsignar] [bit] NOT NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[puntoServicio_id] [int] NULL,
	[usuario_id] [int] NULL,
	[vactual_id] [int] NULL,
	[numTotalAsignado] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histasignaciondet]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histasignaciondet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[lunEnt] [time](7) NULL,
	[lunSal] [time](7) NULL,
	[marEnt] [time](7) NULL,
	[marSal] [time](7) NULL,
	[mieEnt] [time](7) NULL,
	[mieSal] [time](7) NULL,
	[jueEnt] [time](7) NULL,
	[jueSal] [time](7) NULL,
	[vieEnt] [time](7) NULL,
	[vieSal] [time](7) NULL,
	[sabEnt] [time](7) NULL,
	[sabSal] [time](7) NULL,
	[domEnt] [time](7) NULL,
	[domSal] [time](7) NULL,
	[fechaInicio] [date] NULL,
	[fechaFin] [date] NULL,
	[totalHoras] [nvarchar](8) NULL,
	[supervisor] [bit] NOT NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[asignacionCab_id] [int] NULL,
	[operario_id] [int] NULL,
	[perfil_id] [int] NULL,
	[vactual_id] [int] NULL,
	[numTotalHoras] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histnotificacion]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histnotificacion](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaUltimaMod] [datetime2](7) NOT NULL,
	[estado] [nvarchar](30) NOT NULL,
	[cantHorasAprobado] [nvarchar](8) NULL,
	[numCantHorasAprobado] [int] NULL,
	[cantHorasSolicitado] [nvarchar](8) NULL,
	[numCantHorasSolicitado] [int] NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[planificacionEsp_id] [int] NULL,
	[userFiscal_id] [int] NULL,
	[userJefe_id] [int] NULL,
	[usuario_id] [int] NULL,
	[vactual_id] [int] NULL,
	[motivo] [nvarchar](150) NULL,
	[fechaEnvio] [datetime2](7) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histordenserviciocab]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histordenserviciocab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[activo] [bit] NOT NULL,
	[facturar] [bit] NOT NULL,
	[estado] [nvarchar](3) NULL,
	[Fecha] [date] NULL,
	[cantHoras] [nvarchar](8) NULL,
	[numCantHoras] [int] NULL,
	[nroCotizacion] [nvarchar](30) NULL,
	[puntoServicio_id] [int] NULL,
	[tipoOrden_id] [int] NULL,
	[usuario_id] [int] NULL,
	[vactual_id] [int] NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[numHorasDobDiu] [int] NULL,
	[numHorasDobNoc] [int] NULL,
	[numHorasFerDiu] [int] NULL,
	[numHorasFerNoc] [int] NULL,
	[numHorasNorDiu] [int] NULL,
	[numHorasNorNoc] [int] NULL,
	[fechaFin] [date] NULL,
	[numeroOrden] [nvarchar](7) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histordenserviciodet]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histordenserviciodet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[horaInicio] [time](7) NULL,
	[horaFin] [time](7) NULL,
	[fecha] [date] NULL,
	[activo] [bit] NOT NULL,
	[observacion] [nvarchar](200) NOT NULL,
	[operario_id] [int] NULL,
	[ordenServicioCab_id] [int] NULL,
	[usuario_id] [int] NULL,
	[vactual_id] [int] NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[pagoDoble] [bit] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histplanificacioncab]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histplanificacioncab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fecha] [datetime2](7) NOT NULL,
	[cantidad] [int] NULL,
	[cantHoras] [nvarchar](8) NULL,
	[cantHorasNoc] [nvarchar](8) NULL,
	[cantHorasEsp] [nvarchar](8) NULL,
	[rePlanificar] [bit] NOT NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[puntoServicio_id] [int] NULL,
	[vactual_id] [int] NULL,
	[usuario_id] [int] NULL,
	[numCantHoras] [int] NULL,
	[numCantHorasEsp] [int] NULL,
	[numCantHorasNoc] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histplanificacionesp]    Script Date: 19/12/2019 15:07:18 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histplanificacionesp](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[frecuencia] [nvarchar](3) NOT NULL,
	[cantHoras] [nvarchar](8) NULL,
	[fechaLimpProf] [date] NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[especialista_id] [int] NULL,
	[planificacionCab_id] [int] NULL,
	[tipo_id] [int] NULL,
	[vactual_id] [int] NULL,
	[numCantHoras] [int] NULL,
	[estado] [nvarchar](3) NOT NULL,
	[area] [nvarchar](50) NULL,
	[cantidad] [int] NULL,
	[sector] [nvarchar](max) NULL,
	[tipoHora_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histplanificacionope]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histplanificacionope](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[cantidad] [int] NULL,
	[lun] [bit] NOT NULL,
	[mar] [bit] NOT NULL,
	[mie] [bit] NOT NULL,
	[jue] [bit] NOT NULL,
	[vie] [bit] NOT NULL,
	[sab] [bit] NOT NULL,
	[dom] [bit] NOT NULL,
	[fer] [bit] NOT NULL,
	[ent] [time](7) NULL,
	[sal] [time](7) NULL,
	[corte] [nvarchar](8) NULL,
	[total] [nvarchar](8) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[especialista_id] [int] NULL,
	[planificacionCab_id] [int] NULL,
	[vactual_id] [int] NULL,
	[numTotal] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histpuntoservicio]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histpuntoservicio](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[CodPuntoServicio] [nvarchar](50) NOT NULL,
	[NombrePServicio] [nvarchar](100) NOT NULL,
	[DireccionContrato] [nvarchar](150) NOT NULL,
	[Barrios] [nvarchar](70) NOT NULL,
	[Contacto] [nvarchar](100) NOT NULL,
	[MailContacto] [nvarchar](70) NOT NULL,
	[TelefonoContacto] [nvarchar](100) NOT NULL,
	[Coordenadas] [nvarchar](100) NOT NULL,
	[NumeroMarcador] [nvarchar](15) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[Ciudad_id] [int] NOT NULL,
	[Cliente_id] [int] NOT NULL,
	[vactual_id] [int] NULL,
	[activo] [bit] NOT NULL,
	[comentario] [nvarchar](200) NOT NULL,
	[usuario_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histrelevamientocab]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histrelevamientocab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fecha] [datetime2](7) NOT NULL,
	[cantidad] [int] NULL,
	[cantAprendices] [int] NULL,
	[cantidadHrTotal] [nvarchar](8) NULL,
	[cantidadHrEsp] [nvarchar](8) NULL,
	[fechaInicio] [date] NULL,
	[fechaFin] [date] NULL,
	[estado] [nvarchar](30) NOT NULL,
	[comentario] [nvarchar](550) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[puntoServicio_id] [int] NULL,
	[tipoSalario_id] [int] NULL,
	[usuario_id] [int] NULL,
	[vactual_id] [int] NULL,
	[numCantidadHrEsp] [int] NULL,
	[numCantidadHrTotal] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histrelevamientocupohoras]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histrelevamientocupohoras](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[cantHoras] [nvarchar](8) NULL,
	[frecuencia] [nvarchar](3) NOT NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[relevamientoCab_id] [int] NULL,
	[tipoHora_id] [int] NULL,
	[vactual_id] [int] NULL,
	[numCantHoras] [int] NULL,
	[dom] [bit] NOT NULL,
	[jue] [bit] NOT NULL,
	[lun] [bit] NOT NULL,
	[mar] [bit] NOT NULL,
	[mie] [bit] NOT NULL,
	[sab] [bit] NOT NULL,
	[vie] [bit] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histrelevamientodet]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histrelevamientodet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[orden] [int] NULL,
	[lunEnt] [time](7) NULL,
	[lunSal] [time](7) NULL,
	[marEnt] [time](7) NULL,
	[marSal] [time](7) NULL,
	[mieEnt] [time](7) NULL,
	[mieSal] [time](7) NULL,
	[jueEnt] [time](7) NULL,
	[jueSal] [time](7) NULL,
	[vieEnt] [time](7) NULL,
	[vieSal] [time](7) NULL,
	[sabEnt] [time](7) NULL,
	[sabSal] [time](7) NULL,
	[domEnt] [time](7) NULL,
	[domSal] [time](7) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[relevamientoCab_id] [int] NULL,
	[tipoServPart_id] [int] NULL,
	[vactual_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histrelevamientoesp]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histrelevamientoesp](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[frecuencia] [nvarchar](3) NOT NULL,
	[cantHoras] [nvarchar](8) NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[relevamientoCab_id] [int] NULL,
	[tipo_id] [int] NULL,
	[vactual_id] [int] NULL,
	[numCantHoras] [int] NULL,
	[area] [nvarchar](50) NULL,
	[cantidad] [int] NULL,
	[perfil_id] [int] NULL,
	[sector] [nvarchar](max) NULL,
	[tipoHora_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_histrelevamientomensualeros]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_histrelevamientomensualeros](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[mensuCantidad] [int] NULL,
	[sueldo] [int] NULL,
	[vfechaInicio] [datetime2](7) NULL,
	[vfechaFin] [datetime2](7) NULL,
	[vregistro] [int] NULL,
	[relevamientoCab_id] [int] NULL,
	[vactual_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_horariosoperario]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_horariosoperario](
	[idOrden] [int] NOT NULL,
	[diaEntrada] [nvarchar](30) NOT NULL,
	[horaEntrada] [time](7) NOT NULL,
	[diaSalida] [nvarchar](30) NOT NULL,
	[horaSalida] [time](7) NOT NULL,
	[totalHoras] [time](7) NULL,
PRIMARY KEY CLUSTERED 
(
	[idOrden] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_horasnoprocesadas]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_horasnoprocesadas](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[NumCedulaOperario] [nvarchar](30) NOT NULL,
	[Hentrada] [time](7) NULL,
	[Hsalida] [time](7) NULL,
	[total] [time](7) NULL,
	[fecha] [date] NOT NULL,
	[TipoHora] [nvarchar](10) NOT NULL,
	[puntoServicio_id] [int] NOT NULL,
	[comentario] [nvarchar](500) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_horasprocesadas]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_horasprocesadas](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[NumCedulaOperario] [nvarchar](30) NOT NULL,
	[Hentrada] [time](7) NULL,
	[Hsalida] [time](7) NULL,
	[total] [time](7) NULL,
	[fecha] [date] NOT NULL,
	[TipoHora] [nvarchar](10) NOT NULL,
	[comentario] [nvarchar](500) NULL,
	[asignacionDet_id] [int] NULL,
	[puntoServicio_id] [int] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_motivos]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_motivos](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[descripcion] [nvarchar](500) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_nacionalidad]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_nacionalidad](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[Pais] [nvarchar](70) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_notificacion]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_notificacion](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaUltimaMod] [datetime2](7) NOT NULL,
	[estado] [nvarchar](30) NOT NULL,
	[cantHorasAprobado] [nvarchar](8) NULL,
	[numCantHorasAprobado] [int] NULL,
	[cantHorasSolicitado] [nvarchar](8) NULL,
	[numCantHorasSolicitado] [int] NULL,
	[planificacionEsp_id] [int] NULL,
	[userFiscal_id] [int] NULL,
	[userJefe_id] [int] NULL,
	[usuario_id] [int] NULL,
	[motivo] [nvarchar](150) NULL,
	[fechaEnvio] [datetime2](7) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_operariosasignaciondet]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_operariosasignaciondet](
	[id_opeario] [int] NOT NULL,
	[nombres] [nvarchar](200) NOT NULL,
	[nroLegajo] [nvarchar](6) NOT NULL,
	[nombres_puntoServicio] [nvarchar](200) NOT NULL,
	[ids_puntoServicio] [nvarchar](100) NOT NULL,
	[totalHoras] [float] NOT NULL,
	[perfil] [nvarchar](400) NOT NULL,
	[antiguedad] [int] NOT NULL,
	[ids_perfil] [nvarchar](100) NOT NULL,
	[ciudad] [nvarchar](100) NOT NULL,
	[tocaLibre] [nvarchar](10) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id_opeario] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_operariosordenesdet]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_operariosordenesdet](
	[id_opeario] [int] NOT NULL,
	[nombres] [nvarchar](200) NOT NULL,
	[nroLegajo] [nvarchar](6) NOT NULL,
	[nombres_puntoServicio] [nvarchar](200) NOT NULL,
	[ids_puntoServicio] [nvarchar](100) NOT NULL,
	[totalHoras] [float] NOT NULL,
	[perfil] [nvarchar](400) NOT NULL,
	[antiguedad] [int] NOT NULL,
	[ids_perfil] [nvarchar](100) NOT NULL,
	[ciudad] [nvarchar](100) NOT NULL,
	[tocaLibre] [nvarchar](10) NOT NULL,
	[maxAsignacion] [nvarchar](10) NOT NULL,
	[coincideAsignacion] [nvarchar](10) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id_opeario] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_ordenserviciocab]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_ordenserviciocab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[activo] [bit] NOT NULL,
	[facturar] [bit] NOT NULL,
	[estado] [nvarchar](3) NULL,
	[Fecha] [date] NULL,
	[cantHoras] [nvarchar](8) NULL,
	[numCantHoras] [int] NULL,
	[nroCotizacion] [nvarchar](30) NULL,
	[puntoServicio_id] [int] NULL,
	[tipoOrden_id] [int] NULL,
	[usuario_id] [int] NULL,
	[numHorasDobDiu] [int] NULL,
	[numHorasDobNoc] [int] NULL,
	[numHorasFerDiu] [int] NULL,
	[numHorasFerNoc] [int] NULL,
	[numHorasNorDiu] [int] NULL,
	[numHorasNorNoc] [int] NULL,
	[fechaFin] [date] NULL,
	[numeroOrden] [nvarchar](7) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_ordenserviciodet]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_ordenserviciodet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[horaInicio] [time](7) NULL,
	[horaFin] [time](7) NULL,
	[fecha] [date] NULL,
	[activo] [bit] NOT NULL,
	[observacion] [nvarchar](200) NOT NULL,
	[operario_id] [int] NULL,
	[ordenServicioCab_id] [int] NULL,
	[usuario_id] [int] NULL,
	[pagoDoble] [bit] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_parametros]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_parametros](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[tipo] [nvarchar](30) NOT NULL,
	[parametro] [nvarchar](50) NOT NULL,
	[valor] [nvarchar](150) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_planificacioncab]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_planificacioncab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fecha] [datetime2](7) NOT NULL,
	[cantidad] [int] NULL,
	[cantHoras] [nvarchar](8) NULL,
	[cantHorasNoc] [nvarchar](8) NULL,
	[cantHorasEsp] [nvarchar](8) NULL,
	[puntoServicio_id] [int] NULL,
	[rePlanificar] [bit] NOT NULL,
	[usuario_id] [int] NULL,
	[numCantHoras] [int] NULL,
	[numCantHorasEsp] [int] NULL,
	[numCantHorasNoc] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_planificacionesp]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_planificacionesp](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[frecuencia] [nvarchar](3) NOT NULL,
	[especialista_id] [int] NULL,
	[planificacionCab_id] [int] NULL,
	[tipo_id] [int] NULL,
	[cantHoras] [nvarchar](8) NULL,
	[fechaLimpProf] [date] NULL,
	[numCantHoras] [int] NULL,
	[estado] [nvarchar](3) NOT NULL,
	[area] [nvarchar](50) NULL,
	[cantidad] [int] NULL,
	[sector] [nvarchar](max) NULL,
	[tipoHora_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_planificacionope]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_planificacionope](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[cantidad] [int] NULL,
	[lun] [bit] NOT NULL,
	[mar] [bit] NOT NULL,
	[mie] [bit] NOT NULL,
	[jue] [bit] NOT NULL,
	[vie] [bit] NOT NULL,
	[sab] [bit] NOT NULL,
	[dom] [bit] NOT NULL,
	[fer] [bit] NOT NULL,
	[ent] [time](7) NULL,
	[sal] [time](7) NULL,
	[especialista_id] [int] NULL,
	[planificacionCab_id] [int] NULL,
	[corte] [nvarchar](8) NULL,
	[total] [nvarchar](8) NULL,
	[numTotal] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_procesosincronizacion]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_procesosincronizacion](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[mes] [int] NULL,
	[anho] [int] NULL,
	[Fecha] [datetime2](7) NULL,
	[inicioSinc] [datetime2](7) NULL,
	[finSinc] [datetime2](7) NULL,
	[usuario_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_relevamientocab]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_relevamientocab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fecha] [datetime2](7) NOT NULL,
	[cantidad] [int] NULL,
	[puntoServicio_id] [int] NULL,
	[cantidadHrTotal] [nvarchar](8) NULL,
	[cantidadHrEsp] [nvarchar](8) NULL,
	[fechaInicio] [date] NULL,
	[usuario_id] [int] NULL,
	[tipoSalario_id] [int] NULL,
	[comentario] [nvarchar](550) NULL,
	[cantAprendices] [int] NULL,
	[estado] [nvarchar](30) NOT NULL,
	[fechaFin] [date] NULL,
	[numCantidadHrEsp] [int] NULL,
	[numCantidadHrTotal] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_relevamientocupohoras]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_relevamientocupohoras](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[frecuencia] [nvarchar](3) NOT NULL,
	[relevamientoCab_id] [int] NULL,
	[tipoHora_id] [int] NULL,
	[cantHoras] [nvarchar](8) NULL,
	[numCantHoras] [int] NULL,
	[dom] [bit] NOT NULL,
	[jue] [bit] NOT NULL,
	[lun] [bit] NOT NULL,
	[mar] [bit] NOT NULL,
	[mie] [bit] NOT NULL,
	[sab] [bit] NOT NULL,
	[vie] [bit] NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_relevamientodet]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_relevamientodet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[orden] [int] NULL,
	[lunEnt] [time](7) NULL,
	[lunSal] [time](7) NULL,
	[marEnt] [time](7) NULL,
	[marSal] [time](7) NULL,
	[mieEnt] [time](7) NULL,
	[mieSal] [time](7) NULL,
	[jueEnt] [time](7) NULL,
	[jueSal] [time](7) NULL,
	[vieEnt] [time](7) NULL,
	[vieSal] [time](7) NULL,
	[sabEnt] [time](7) NULL,
	[sabSal] [time](7) NULL,
	[domEnt] [time](7) NULL,
	[domSal] [time](7) NULL,
	[relevamientoCab_id] [int] NULL,
	[tipoServPart_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_relevamientoesp]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_relevamientoesp](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[frecuencia] [nvarchar](3) NOT NULL,
	[relevamientoCab_id] [int] NULL,
	[tipo_id] [int] NULL,
	[cantHoras] [nvarchar](8) NULL,
	[numCantHoras] [int] NULL,
	[area] [nvarchar](50) NULL,
	[cantidad] [int] NULL,
	[perfil_id] [int] NULL,
	[sector] [nvarchar](max) NULL,
	[tipoHora_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_relevamientomensualeros]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_relevamientomensualeros](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[mensuCantidad] [int] NULL,
	[sueldo] [int] NULL,
	[relevamientoCab_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_remplazomanresp]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_remplazomanresp](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaRetorno] [date] NULL,
	[comentarios] [nvarchar](1000) NOT NULL,
	[fecha_creacion] [datetime2](7) NULL,
	[id_reemplazo_id] [int] NULL,
	[motivo_id] [int] NULL,
	[usuario_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_remplazoscab]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_remplazoscab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fechaInicio] [date] NULL,
	[fechaFin] [date] NULL,
	[FechaHoraRemplazo] [datetime2](7) NOT NULL,
	[tipoRemplazo] [nvarchar](15) NOT NULL,
	[usuario_id] [int] NULL,
	[alertaId_id] [int] NULL,
	[fecha_creacion] [datetime2](7) NULL,
	[operario_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_remplazosdet]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_remplazosdet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[fecha] [date] NULL,
	[Asignacion_id] [int] NULL,
	[remplazo_id] [int] NOT NULL,
	[remplazoCab_id] [int] NULL,
	[fechaFin] [date] NULL,
	[diaRemplazo] [nvarchar](15) NOT NULL,
	[puntoServicio_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_sincronizacioncab]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_sincronizacioncab](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[nombrePersona] [nvarchar](100) NULL,
	[mes] [int] NULL,
	[anho] [int] NULL,
	[Fecha] [datetime2](7) NULL,
	[cantidad] [float] NULL,
	[enviado] [bit] NOT NULL,
	[operario_id] [int] NULL,
	[proceso_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_sincronizaciondet]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_sincronizaciondet](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[CodPersona] [nvarchar](10) NULL,
	[tipoHora] [nvarchar](10) NULL,
	[CodUbicacion] [nvarchar](30) NULL,
	[cantidad] [float] NULL,
	[operario_id] [int] NULL,
	[puntoServicio_id] [int] NULL,
	[sincronizacionCab_id] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_tipohorario]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_tipohorario](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[tipoHorario] [nvarchar](50) NOT NULL,
	[horaInicio] [time](7) NULL,
	[horaFin] [time](7) NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_tipoorden]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_tipoorden](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[tipoOrden] [nvarchar](50) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_tiposalario]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_tiposalario](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[tipoSalario] [nvarchar](50) NOT NULL,
	[descripcion] [nvarchar](200) NULL,
	[valor] [int] NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_tiposervicio]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_tiposervicio](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[tipoServicio] [nvarchar](200) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Operarios_tiposervicioparticular]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Operarios_tiposervicioparticular](
	[id] [int] IDENTITY(1,1) NOT NULL,
	[tipoServicioParticular] [nvarchar](100) NOT NULL,
PRIMARY KEY CLUSTERED 
(
	[id] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
) ON [PRIMARY]
GO
ALTER TABLE [dbo].[auth_group_permissions]  WITH NOCHECK ADD  CONSTRAINT [auth_group_permissions_group_id_b120cbf9_fk_auth_group_id] FOREIGN KEY([group_id])
REFERENCES [dbo].[auth_group] ([id])
GO
ALTER TABLE [dbo].[auth_group_permissions] CHECK CONSTRAINT [auth_group_permissions_group_id_b120cbf9_fk_auth_group_id]
GO
ALTER TABLE [dbo].[auth_group_permissions]  WITH NOCHECK ADD  CONSTRAINT [auth_group_permissions_permission_id_84c5c92e_fk_auth_permission_id] FOREIGN KEY([permission_id])
REFERENCES [dbo].[auth_permission] ([id])
GO
ALTER TABLE [dbo].[auth_group_permissions] CHECK CONSTRAINT [auth_group_permissions_permission_id_84c5c92e_fk_auth_permission_id]
GO
ALTER TABLE [dbo].[auth_permission]  WITH NOCHECK ADD  CONSTRAINT [auth_permission_content_type_id_2f476e4b_fk_django_content_type_id] FOREIGN KEY([content_type_id])
REFERENCES [dbo].[django_content_type] ([id])
GO
ALTER TABLE [dbo].[auth_permission] CHECK CONSTRAINT [auth_permission_content_type_id_2f476e4b_fk_django_content_type_id]
GO
ALTER TABLE [dbo].[auth_user_groups]  WITH NOCHECK ADD  CONSTRAINT [auth_user_groups_group_id_97559544_fk_auth_group_id] FOREIGN KEY([group_id])
REFERENCES [dbo].[auth_group] ([id])
GO
ALTER TABLE [dbo].[auth_user_groups] CHECK CONSTRAINT [auth_user_groups_group_id_97559544_fk_auth_group_id]
GO
ALTER TABLE [dbo].[auth_user_groups]  WITH NOCHECK ADD  CONSTRAINT [auth_user_groups_user_id_6a12ed8b_fk_auth_user_id] FOREIGN KEY([user_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[auth_user_groups] CHECK CONSTRAINT [auth_user_groups_user_id_6a12ed8b_fk_auth_user_id]
GO
ALTER TABLE [dbo].[auth_user_user_permissions]  WITH NOCHECK ADD  CONSTRAINT [auth_user_user_permissions_permission_id_1fbb5f2c_fk_auth_permission_id] FOREIGN KEY([permission_id])
REFERENCES [dbo].[auth_permission] ([id])
GO
ALTER TABLE [dbo].[auth_user_user_permissions] CHECK CONSTRAINT [auth_user_user_permissions_permission_id_1fbb5f2c_fk_auth_permission_id]
GO
ALTER TABLE [dbo].[auth_user_user_permissions]  WITH NOCHECK ADD  CONSTRAINT [auth_user_user_permissions_user_id_a95ead1b_fk_auth_user_id] FOREIGN KEY([user_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[auth_user_user_permissions] CHECK CONSTRAINT [auth_user_user_permissions_user_id_a95ead1b_fk_auth_user_id]
GO
ALTER TABLE [dbo].[django_admin_log]  WITH NOCHECK ADD  CONSTRAINT [django_admin_log_content_type_id_c4bce8eb_fk_django_content_type_id] FOREIGN KEY([content_type_id])
REFERENCES [dbo].[django_content_type] ([id])
GO
ALTER TABLE [dbo].[django_admin_log] CHECK CONSTRAINT [django_admin_log_content_type_id_c4bce8eb_fk_django_content_type_id]
GO
ALTER TABLE [dbo].[django_admin_log]  WITH NOCHECK ADD  CONSTRAINT [django_admin_log_user_id_c564eba6_fk_auth_user_id] FOREIGN KEY([user_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[django_admin_log] CHECK CONSTRAINT [django_admin_log_user_id_c564eba6_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_alertaresp]  WITH CHECK ADD  CONSTRAINT [Operarios_alertaresp_id_alerta_id_3f5b2970_fk_Operarios_alertas_id] FOREIGN KEY([id_alerta_id])
REFERENCES [dbo].[Operarios_alertas] ([id])
GO
ALTER TABLE [dbo].[Operarios_alertaresp] CHECK CONSTRAINT [Operarios_alertaresp_id_alerta_id_3f5b2970_fk_Operarios_alertas_id]
GO
ALTER TABLE [dbo].[Operarios_alertaresp]  WITH CHECK ADD  CONSTRAINT [Operarios_alertaresp_id_reemplazo_id_925aaec5_fk_Operarios_remplazoscab_id] FOREIGN KEY([id_reemplazo_id])
REFERENCES [dbo].[Operarios_remplazoscab] ([id])
GO
ALTER TABLE [dbo].[Operarios_alertaresp] CHECK CONSTRAINT [Operarios_alertaresp_id_reemplazo_id_925aaec5_fk_Operarios_remplazoscab_id]
GO
ALTER TABLE [dbo].[Operarios_alertaresp]  WITH CHECK ADD  CONSTRAINT [Operarios_alertaresp_motivo_id_50e0d857_fk_Operarios_motivos_id] FOREIGN KEY([motivo_id])
REFERENCES [dbo].[Operarios_motivos] ([id])
GO
ALTER TABLE [dbo].[Operarios_alertaresp] CHECK CONSTRAINT [Operarios_alertaresp_motivo_id_50e0d857_fk_Operarios_motivos_id]
GO
ALTER TABLE [dbo].[Operarios_alertaresp]  WITH CHECK ADD  CONSTRAINT [Operarios_alertaresp_usuario_id_14c3c06e_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_alertaresp] CHECK CONSTRAINT [Operarios_alertaresp_usuario_id_14c3c06e_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_alertas]  WITH CHECK ADD  CONSTRAINT [Operarios_alertas_Asignacion_id_6691da40_fk_Operarios_asignaciondet_id] FOREIGN KEY([Asignacion_id])
REFERENCES [dbo].[Operarios_asignaciondet] ([id])
GO
ALTER TABLE [dbo].[Operarios_alertas] CHECK CONSTRAINT [Operarios_alertas_Asignacion_id_6691da40_fk_Operarios_asignaciondet_id]
GO
ALTER TABLE [dbo].[Operarios_alertas]  WITH CHECK ADD  CONSTRAINT [Operarios_alertas_Operario_id_715e0c3f_fk_Operarios_operario_id] FOREIGN KEY([Operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_alertas] CHECK CONSTRAINT [Operarios_alertas_Operario_id_715e0c3f_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_alertas]  WITH CHECK ADD  CONSTRAINT [Operarios_alertas_PuntoServicio_id_f7951021_fk_Operarios_puntoservicio_id] FOREIGN KEY([PuntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_alertas] CHECK CONSTRAINT [Operarios_alertas_PuntoServicio_id_f7951021_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_asigfiscalpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_asigfiscalpuntoservicio_puntoServicio_id_17c1e980_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_asigfiscalpuntoservicio] CHECK CONSTRAINT [Operarios_asigfiscalpuntoservicio_puntoServicio_id_17c1e980_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_asigfiscalpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_asigfiscalpuntoservicio_userFiscal_id_2901eb04_fk_auth_user_id] FOREIGN KEY([userFiscal_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_asigfiscalpuntoservicio] CHECK CONSTRAINT [Operarios_asigfiscalpuntoservicio_userFiscal_id_2901eb04_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_asigjefefiscal]  WITH CHECK ADD  CONSTRAINT [Operarios_asigjefefiscal_userFiscal_id_fd629b15_fk_auth_user_id] FOREIGN KEY([userFiscal_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_asigjefefiscal] CHECK CONSTRAINT [Operarios_asigjefefiscal_userFiscal_id_fd629b15_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_asigjefefiscal]  WITH CHECK ADD  CONSTRAINT [Operarios_asigjefefiscal_userJefe_id_11881985_fk_auth_user_id] FOREIGN KEY([userJefe_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_asigjefefiscal] CHECK CONSTRAINT [Operarios_asigjefefiscal_userJefe_id_11881985_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_asignacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_asignacioncab_puntoServicio_id_0edcb2d4_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignacioncab] CHECK CONSTRAINT [Operarios_asignacioncab_puntoServicio_id_0edcb2d4_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_asignacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_asignacioncab_usuario_id_f0550d64_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignacioncab] CHECK CONSTRAINT [Operarios_asignacioncab_usuario_id_f0550d64_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_asignaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_asignaciondet_asignacionCab_id_2e6108ef_fk_Operarios_asignacioncab_id] FOREIGN KEY([asignacionCab_id])
REFERENCES [dbo].[Operarios_asignacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignaciondet] CHECK CONSTRAINT [Operarios_asignaciondet_asignacionCab_id_2e6108ef_fk_Operarios_asignacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_asignaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_asignaciondet_operario_id_05faeb8e_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignaciondet] CHECK CONSTRAINT [Operarios_asignaciondet_operario_id_05faeb8e_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_asignaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_asignaciondet_perfil_id_a44d1ff8_fk_Operarios_especializacion_id] FOREIGN KEY([perfil_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignaciondet] CHECK CONSTRAINT [Operarios_asignaciondet_perfil_id_a44d1ff8_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp]  WITH CHECK ADD  CONSTRAINT [Operarios_asignaciondettemp_asignacionCab_id_b5e02ce1_fk_Operarios_asignacioncab_id] FOREIGN KEY([asignacionCab_id])
REFERENCES [dbo].[Operarios_asignacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp] CHECK CONSTRAINT [Operarios_asignaciondettemp_asignacionCab_id_b5e02ce1_fk_Operarios_asignacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp]  WITH CHECK ADD  CONSTRAINT [Operarios_asignaciondettemp_asignacionDet_original_id_0ffdf913_fk_Operarios_asignaciondet_id] FOREIGN KEY([asignacionDet_original_id])
REFERENCES [dbo].[Operarios_asignaciondet] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp] CHECK CONSTRAINT [Operarios_asignaciondettemp_asignacionDet_original_id_0ffdf913_fk_Operarios_asignaciondet_id]
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp]  WITH CHECK ADD  CONSTRAINT [Operarios_asignaciondettemp_operario_id_f768220e_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp] CHECK CONSTRAINT [Operarios_asignaciondettemp_operario_id_f768220e_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp]  WITH CHECK ADD  CONSTRAINT [Operarios_asignaciondettemp_perfil_id_57c29b88_fk_Operarios_especializacion_id] FOREIGN KEY([perfil_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp] CHECK CONSTRAINT [Operarios_asignaciondettemp_perfil_id_57c29b88_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp]  WITH CHECK ADD  CONSTRAINT [Operarios_asignaciondettemp_remplazosCab_id_de68a164_fk_Operarios_remplazoscab_id] FOREIGN KEY([remplazosCab_id])
REFERENCES [dbo].[Operarios_remplazoscab] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignaciondettemp] CHECK CONSTRAINT [Operarios_asignaciondettemp_remplazosCab_id_de68a164_fk_Operarios_remplazoscab_id]
GO
ALTER TABLE [dbo].[Operarios_asignacionesprocesadas]  WITH CHECK ADD  CONSTRAINT [Operarios_asignacionesprocesadas_asignacionDet_id_b51e7e70_fk_Operarios_asignaciondet_id] FOREIGN KEY([asignacionDet_id])
REFERENCES [dbo].[Operarios_asignaciondet] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignacionesprocesadas] CHECK CONSTRAINT [Operarios_asignacionesprocesadas_asignacionDet_id_b51e7e70_fk_Operarios_asignaciondet_id]
GO
ALTER TABLE [dbo].[Operarios_asignacionesprocesadas]  WITH CHECK ADD  CONSTRAINT [Operarios_asignacionesprocesadas_puntoServicio_id_0a2e596d_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_asignacionesprocesadas] CHECK CONSTRAINT [Operarios_asignacionesprocesadas_puntoServicio_id_0a2e596d_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_cargoasignado]  WITH CHECK ADD  CONSTRAINT [Operarios_cargoasignado_cargo_id_ae4285ce_fk_Operarios_cargo_id] FOREIGN KEY([cargo_id])
REFERENCES [dbo].[Operarios_cargo] ([id])
GO
ALTER TABLE [dbo].[Operarios_cargoasignado] CHECK CONSTRAINT [Operarios_cargoasignado_cargo_id_ae4285ce_fk_Operarios_cargo_id]
GO
ALTER TABLE [dbo].[Operarios_cargoasignado]  WITH CHECK ADD  CONSTRAINT [Operarios_cargoasignado_user_id_39a10e36_fk_auth_user_id] FOREIGN KEY([user_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_cargoasignado] CHECK CONSTRAINT [Operarios_cargoasignado_user_id_39a10e36_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_cliente]  WITH CHECK ADD  CONSTRAINT [Operarios_cliente_GrupoEmpresarial_id_53fabde3_fk_Operarios_grupoempresarial_id] FOREIGN KEY([GrupoEmpresarial_id])
REFERENCES [dbo].[Operarios_grupoempresarial] ([id])
GO
ALTER TABLE [dbo].[Operarios_cliente] CHECK CONSTRAINT [Operarios_cliente_GrupoEmpresarial_id_53fabde3_fk_Operarios_grupoempresarial_id]
GO
ALTER TABLE [dbo].[Operarios_cuporeal]  WITH CHECK ADD  CONSTRAINT [Operarios_cuporeal_puntoServicio_id_3c20b006_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_cuporeal] CHECK CONSTRAINT [Operarios_cuporeal_puntoServicio_id_3c20b006_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_cupoutilizado]  WITH CHECK ADD  CONSTRAINT [Operarios_cupoutilizado_horasProcesadas_id_cc4cdaa7_fk_Operarios_horasprocesadas_id] FOREIGN KEY([horasProcesadas_id])
REFERENCES [dbo].[Operarios_horasprocesadas] ([id])
GO
ALTER TABLE [dbo].[Operarios_cupoutilizado] CHECK CONSTRAINT [Operarios_cupoutilizado_horasProcesadas_id_cc4cdaa7_fk_Operarios_horasprocesadas_id]
GO
ALTER TABLE [dbo].[Operarios_cupoutilizado]  WITH CHECK ADD  CONSTRAINT [Operarios_cupoutilizado_puntoServicio_id_a2388b3f_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_cupoutilizado] CHECK CONSTRAINT [Operarios_cupoutilizado_puntoServicio_id_a2388b3f_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_dialibre]  WITH CHECK ADD  CONSTRAINT [Operarios_dialibre_id_operario_id_797c52c3_fk_Operarios_operario_id] FOREIGN KEY([id_operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_dialibre] CHECK CONSTRAINT [Operarios_dialibre_id_operario_id_797c52c3_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_hisasigfiscalpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_hisasigfiscalpuntoservicio_puntoServicio_id_c31589cc_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_hisasigfiscalpuntoservicio] CHECK CONSTRAINT [Operarios_hisasigfiscalpuntoservicio_puntoServicio_id_c31589cc_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_hisasigfiscalpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_hisasigfiscalpuntoservicio_userFiscal_id_afbfedcd_fk_auth_user_id] FOREIGN KEY([userFiscal_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_hisasigfiscalpuntoservicio] CHECK CONSTRAINT [Operarios_hisasigfiscalpuntoservicio_userFiscal_id_afbfedcd_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_hisasigjefefiscal]  WITH CHECK ADD  CONSTRAINT [Operarios_hisasigjefefiscal_userFiscal_id_51528192_fk_auth_user_id] FOREIGN KEY([userFiscal_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_hisasigjefefiscal] CHECK CONSTRAINT [Operarios_hisasigjefefiscal_userFiscal_id_51528192_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_hisasigjefefiscal]  WITH CHECK ADD  CONSTRAINT [Operarios_hisasigjefefiscal_userJefe_id_ce19790f_fk_auth_user_id] FOREIGN KEY([userJefe_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_hisasigjefefiscal] CHECK CONSTRAINT [Operarios_hisasigjefefiscal_userJefe_id_ce19790f_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histactividadcab]  WITH CHECK ADD  CONSTRAINT [Operarios_histactividadcab_planificacionEsp_id_34605d40_fk_Operarios_planificacionesp_id] FOREIGN KEY([planificacionEsp_id])
REFERENCES [dbo].[Operarios_planificacionesp] ([id])
GO
ALTER TABLE [dbo].[Operarios_histactividadcab] CHECK CONSTRAINT [Operarios_histactividadcab_planificacionEsp_id_34605d40_fk_Operarios_planificacionesp_id]
GO
ALTER TABLE [dbo].[Operarios_histactividadcab]  WITH CHECK ADD  CONSTRAINT [Operarios_histactividadcab_usuario_id_8ff03e2f_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histactividadcab] CHECK CONSTRAINT [Operarios_histactividadcab_usuario_id_8ff03e2f_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histactividadcab]  WITH CHECK ADD  CONSTRAINT [Operarios_histactividadcab_vactual_id_1fa32eba_fk_Operarios_actividadcab_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_actividadcab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histactividadcab] CHECK CONSTRAINT [Operarios_histactividadcab_vactual_id_1fa32eba_fk_Operarios_actividadcab_id]
GO
ALTER TABLE [dbo].[Operarios_histactividaddet]  WITH CHECK ADD  CONSTRAINT [Operarios_histactividaddet_actividadCab_id_6fc9913d_fk_Operarios_actividadcab_id] FOREIGN KEY([actividadCab_id])
REFERENCES [dbo].[Operarios_actividadcab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histactividaddet] CHECK CONSTRAINT [Operarios_histactividaddet_actividadCab_id_6fc9913d_fk_Operarios_actividadcab_id]
GO
ALTER TABLE [dbo].[Operarios_histactividaddet]  WITH CHECK ADD  CONSTRAINT [Operarios_histactividaddet_operario_id_fba7dd3a_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_histactividaddet] CHECK CONSTRAINT [Operarios_histactividaddet_operario_id_fba7dd3a_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_histactividaddet]  WITH CHECK ADD  CONSTRAINT [Operarios_histactividaddet_perfil_id_6290e99d_fk_Operarios_especializacion_id] FOREIGN KEY([perfil_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_histactividaddet] CHECK CONSTRAINT [Operarios_histactividaddet_perfil_id_6290e99d_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_histactividaddet]  WITH CHECK ADD  CONSTRAINT [Operarios_histactividaddet_vactual_id_445f0b2d_fk_Operarios_actividaddet_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_actividaddet] ([id])
GO
ALTER TABLE [dbo].[Operarios_histactividaddet] CHECK CONSTRAINT [Operarios_histactividaddet_vactual_id_445f0b2d_fk_Operarios_actividaddet_id]
GO
ALTER TABLE [dbo].[Operarios_histasigfiscalpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_histasigfiscalpuntoservicio_puntoServicio_id_9e30b33b_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasigfiscalpuntoservicio] CHECK CONSTRAINT [Operarios_histasigfiscalpuntoservicio_puntoServicio_id_9e30b33b_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_histasigfiscalpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_histasigfiscalpuntoservicio_userFiscal_id_cbe642a4_fk_auth_user_id] FOREIGN KEY([userFiscal_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasigfiscalpuntoservicio] CHECK CONSTRAINT [Operarios_histasigfiscalpuntoservicio_userFiscal_id_cbe642a4_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histasigfiscalpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_histasigfiscalpuntoservicio_vactual_id_bea12ac0_fk_Operarios_asigfiscalpuntoservicio_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_asigfiscalpuntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasigfiscalpuntoservicio] CHECK CONSTRAINT [Operarios_histasigfiscalpuntoservicio_vactual_id_bea12ac0_fk_Operarios_asigfiscalpuntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_histasigjefefiscal]  WITH CHECK ADD  CONSTRAINT [Operarios_histasigjefefiscal_userFiscal_id_a44964ec_fk_auth_user_id] FOREIGN KEY([userFiscal_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasigjefefiscal] CHECK CONSTRAINT [Operarios_histasigjefefiscal_userFiscal_id_a44964ec_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histasigjefefiscal]  WITH CHECK ADD  CONSTRAINT [Operarios_histasigjefefiscal_userJefe_id_f83554b0_fk_auth_user_id] FOREIGN KEY([userJefe_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasigjefefiscal] CHECK CONSTRAINT [Operarios_histasigjefefiscal_userJefe_id_f83554b0_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histasigjefefiscal]  WITH CHECK ADD  CONSTRAINT [Operarios_histasigjefefiscal_vactual_id_d00540b8_fk_Operarios_asigjefefiscal_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_asigjefefiscal] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasigjefefiscal] CHECK CONSTRAINT [Operarios_histasigjefefiscal_vactual_id_d00540b8_fk_Operarios_asigjefefiscal_id]
GO
ALTER TABLE [dbo].[Operarios_histasignacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_histasignacioncab_puntoServicio_id_fde55dc2_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasignacioncab] CHECK CONSTRAINT [Operarios_histasignacioncab_puntoServicio_id_fde55dc2_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_histasignacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_histasignacioncab_usuario_id_5e1331dc_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasignacioncab] CHECK CONSTRAINT [Operarios_histasignacioncab_usuario_id_5e1331dc_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histasignacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_histasignacioncab_vactual_id_8e09d320_fk_Operarios_asignacioncab_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_asignacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasignacioncab] CHECK CONSTRAINT [Operarios_histasignacioncab_vactual_id_8e09d320_fk_Operarios_asignacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_histasignaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_histasignaciondet_asignacionCab_id_96dc1c94_fk_Operarios_asignacioncab_id] FOREIGN KEY([asignacionCab_id])
REFERENCES [dbo].[Operarios_asignacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasignaciondet] CHECK CONSTRAINT [Operarios_histasignaciondet_asignacionCab_id_96dc1c94_fk_Operarios_asignacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_histasignaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_histasignaciondet_operario_id_c8e65c83_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasignaciondet] CHECK CONSTRAINT [Operarios_histasignaciondet_operario_id_c8e65c83_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_histasignaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_histasignaciondet_perfil_id_b6a7e6ef_fk_Operarios_especializacion_id] FOREIGN KEY([perfil_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasignaciondet] CHECK CONSTRAINT [Operarios_histasignaciondet_perfil_id_b6a7e6ef_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_histasignaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_histasignaciondet_vactual_id_7e1169c7_fk_Operarios_asignaciondet_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_asignaciondet] ([id])
GO
ALTER TABLE [dbo].[Operarios_histasignaciondet] CHECK CONSTRAINT [Operarios_histasignaciondet_vactual_id_7e1169c7_fk_Operarios_asignaciondet_id]
GO
ALTER TABLE [dbo].[Operarios_histnotificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_histnotificacion_planificacionEsp_id_14b556c5_fk_Operarios_planificacionesp_id] FOREIGN KEY([planificacionEsp_id])
REFERENCES [dbo].[Operarios_planificacionesp] ([id])
GO
ALTER TABLE [dbo].[Operarios_histnotificacion] CHECK CONSTRAINT [Operarios_histnotificacion_planificacionEsp_id_14b556c5_fk_Operarios_planificacionesp_id]
GO
ALTER TABLE [dbo].[Operarios_histnotificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_histnotificacion_userFiscal_id_d4a57ba7_fk_auth_user_id] FOREIGN KEY([userFiscal_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histnotificacion] CHECK CONSTRAINT [Operarios_histnotificacion_userFiscal_id_d4a57ba7_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histnotificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_histnotificacion_userJefe_id_b311d511_fk_auth_user_id] FOREIGN KEY([userJefe_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histnotificacion] CHECK CONSTRAINT [Operarios_histnotificacion_userJefe_id_b311d511_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histnotificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_histnotificacion_usuario_id_0b8703b6_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histnotificacion] CHECK CONSTRAINT [Operarios_histnotificacion_usuario_id_0b8703b6_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histnotificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_histnotificacion_vactual_id_8c3edfbf_fk_Operarios_notificacion_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_notificacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_histnotificacion] CHECK CONSTRAINT [Operarios_histnotificacion_vactual_id_8c3edfbf_fk_Operarios_notificacion_id]
GO
ALTER TABLE [dbo].[Operarios_histordenserviciocab]  WITH CHECK ADD  CONSTRAINT [Operarios_histordenserviciocab_puntoServicio_id_3f691690_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histordenserviciocab] CHECK CONSTRAINT [Operarios_histordenserviciocab_puntoServicio_id_3f691690_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_histordenserviciocab]  WITH CHECK ADD  CONSTRAINT [Operarios_histordenserviciocab_tipoOrden_id_ee893e7b_fk_Operarios_tipoorden_id] FOREIGN KEY([tipoOrden_id])
REFERENCES [dbo].[Operarios_tipoorden] ([id])
GO
ALTER TABLE [dbo].[Operarios_histordenserviciocab] CHECK CONSTRAINT [Operarios_histordenserviciocab_tipoOrden_id_ee893e7b_fk_Operarios_tipoorden_id]
GO
ALTER TABLE [dbo].[Operarios_histordenserviciocab]  WITH CHECK ADD  CONSTRAINT [Operarios_histordenserviciocab_usuario_id_54283871_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histordenserviciocab] CHECK CONSTRAINT [Operarios_histordenserviciocab_usuario_id_54283871_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histordenserviciocab]  WITH CHECK ADD  CONSTRAINT [Operarios_histordenserviciocab_vactual_id_163ff289_fk_Operarios_ordenserviciocab_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_ordenserviciocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histordenserviciocab] CHECK CONSTRAINT [Operarios_histordenserviciocab_vactual_id_163ff289_fk_Operarios_ordenserviciocab_id]
GO
ALTER TABLE [dbo].[Operarios_histordenserviciodet]  WITH CHECK ADD  CONSTRAINT [Operarios_histordenserviciodet_operario_id_6786d117_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_histordenserviciodet] CHECK CONSTRAINT [Operarios_histordenserviciodet_operario_id_6786d117_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_histordenserviciodet]  WITH CHECK ADD  CONSTRAINT [Operarios_histordenserviciodet_ordenServicioCab_id_ff4a4c57_fk_Operarios_ordenserviciocab_id] FOREIGN KEY([ordenServicioCab_id])
REFERENCES [dbo].[Operarios_ordenserviciocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histordenserviciodet] CHECK CONSTRAINT [Operarios_histordenserviciodet_ordenServicioCab_id_ff4a4c57_fk_Operarios_ordenserviciocab_id]
GO
ALTER TABLE [dbo].[Operarios_histordenserviciodet]  WITH CHECK ADD  CONSTRAINT [Operarios_histordenserviciodet_usuario_id_7864916d_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histordenserviciodet] CHECK CONSTRAINT [Operarios_histordenserviciodet_usuario_id_7864916d_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histordenserviciodet]  WITH CHECK ADD  CONSTRAINT [Operarios_histordenserviciodet_vactual_id_48d8470a_fk_Operarios_ordenserviciodet_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_ordenserviciodet] ([id])
GO
ALTER TABLE [dbo].[Operarios_histordenserviciodet] CHECK CONSTRAINT [Operarios_histordenserviciodet_vactual_id_48d8470a_fk_Operarios_ordenserviciodet_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacioncab_puntoServicio_id_95a158f2_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacioncab] CHECK CONSTRAINT [Operarios_histplanificacioncab_puntoServicio_id_95a158f2_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacioncab_usuario_id_b4eddd87_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacioncab] CHECK CONSTRAINT [Operarios_histplanificacioncab_usuario_id_b4eddd87_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacioncab_vactual_id_dd8f9bf5_fk_Operarios_planificacioncab_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_planificacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacioncab] CHECK CONSTRAINT [Operarios_histplanificacioncab_vactual_id_dd8f9bf5_fk_Operarios_planificacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacionesp_especialista_id_50df9702_fk_Operarios_especializacion_id] FOREIGN KEY([especialista_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp] CHECK CONSTRAINT [Operarios_histplanificacionesp_especialista_id_50df9702_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacionesp_planificacionCab_id_e57bc9c8_fk_Operarios_planificacioncab_id] FOREIGN KEY([planificacionCab_id])
REFERENCES [dbo].[Operarios_planificacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp] CHECK CONSTRAINT [Operarios_histplanificacionesp_planificacionCab_id_e57bc9c8_fk_Operarios_planificacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacionesp_tipo_id_156fc3e1_fk_Operarios_tiposervicio_id] FOREIGN KEY([tipo_id])
REFERENCES [dbo].[Operarios_tiposervicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp] CHECK CONSTRAINT [Operarios_histplanificacionesp_tipo_id_156fc3e1_fk_Operarios_tiposervicio_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacionesp_tipoHora_id_8672a930_fk_Operarios_tipohorario_id] FOREIGN KEY([tipoHora_id])
REFERENCES [dbo].[Operarios_tipohorario] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp] CHECK CONSTRAINT [Operarios_histplanificacionesp_tipoHora_id_8672a930_fk_Operarios_tipohorario_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacionesp_vactual_id_148c5151_fk_Operarios_planificacionesp_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_planificacionesp] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacionesp] CHECK CONSTRAINT [Operarios_histplanificacionesp_vactual_id_148c5151_fk_Operarios_planificacionesp_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacionope]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacionope_especialista_id_270e1b8e_fk_Operarios_especializacion_id] FOREIGN KEY([especialista_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacionope] CHECK CONSTRAINT [Operarios_histplanificacionope_especialista_id_270e1b8e_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacionope]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacionope_planificacionCab_id_b3fe95d1_fk_Operarios_planificacioncab_id] FOREIGN KEY([planificacionCab_id])
REFERENCES [dbo].[Operarios_planificacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacionope] CHECK CONSTRAINT [Operarios_histplanificacionope_planificacionCab_id_b3fe95d1_fk_Operarios_planificacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_histplanificacionope]  WITH CHECK ADD  CONSTRAINT [Operarios_histplanificacionope_vactual_id_eb99ca56_fk_Operarios_planificacionope_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_planificacionope] ([id])
GO
ALTER TABLE [dbo].[Operarios_histplanificacionope] CHECK CONSTRAINT [Operarios_histplanificacionope_vactual_id_eb99ca56_fk_Operarios_planificacionope_id]
GO
ALTER TABLE [dbo].[Operarios_histpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_histpuntoservicio_Ciudad_id_6c89efb8_fk_Operarios_ciudad_id] FOREIGN KEY([Ciudad_id])
REFERENCES [dbo].[Operarios_ciudad] ([id])
GO
ALTER TABLE [dbo].[Operarios_histpuntoservicio] CHECK CONSTRAINT [Operarios_histpuntoservicio_Ciudad_id_6c89efb8_fk_Operarios_ciudad_id]
GO
ALTER TABLE [dbo].[Operarios_histpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_histpuntoservicio_Cliente_id_d9b1edc4_fk_Operarios_cliente_id] FOREIGN KEY([Cliente_id])
REFERENCES [dbo].[Operarios_cliente] ([id])
GO
ALTER TABLE [dbo].[Operarios_histpuntoservicio] CHECK CONSTRAINT [Operarios_histpuntoservicio_Cliente_id_d9b1edc4_fk_Operarios_cliente_id]
GO
ALTER TABLE [dbo].[Operarios_histpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_histpuntoservicio_usuario_id_14ceeb3c_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histpuntoservicio] CHECK CONSTRAINT [Operarios_histpuntoservicio_usuario_id_14ceeb3c_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histpuntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_histpuntoservicio_vactual_id_20e92343_fk_Operarios_puntoservicio_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histpuntoservicio] CHECK CONSTRAINT [Operarios_histpuntoservicio_vactual_id_20e92343_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocab]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientocab_puntoServicio_id_d55bc49f_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocab] CHECK CONSTRAINT [Operarios_histrelevamientocab_puntoServicio_id_d55bc49f_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocab]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientocab_tipoSalario_id_950fe0a5_fk_Operarios_tiposalario_id] FOREIGN KEY([tipoSalario_id])
REFERENCES [dbo].[Operarios_tiposalario] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocab] CHECK CONSTRAINT [Operarios_histrelevamientocab_tipoSalario_id_950fe0a5_fk_Operarios_tiposalario_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocab]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientocab_usuario_id_4c327993_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocab] CHECK CONSTRAINT [Operarios_histrelevamientocab_usuario_id_4c327993_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocab]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientocab_vactual_id_eb8f814d_fk_Operarios_relevamientocab_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocab] CHECK CONSTRAINT [Operarios_histrelevamientocab_vactual_id_eb8f814d_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocupohoras]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientocupohoras_relevamientoCab_id_bfbcb6a4_fk_Operarios_relevamientocab_id] FOREIGN KEY([relevamientoCab_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocupohoras] CHECK CONSTRAINT [Operarios_histrelevamientocupohoras_relevamientoCab_id_bfbcb6a4_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocupohoras]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientocupohoras_tipoHora_id_6fa7989f_fk_Operarios_tipohorario_id] FOREIGN KEY([tipoHora_id])
REFERENCES [dbo].[Operarios_tipohorario] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocupohoras] CHECK CONSTRAINT [Operarios_histrelevamientocupohoras_tipoHora_id_6fa7989f_fk_Operarios_tipohorario_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocupohoras]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientocupohoras_vactual_id_5d337dac_fk_Operarios_relevamientocupohoras_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_relevamientocupohoras] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientocupohoras] CHECK CONSTRAINT [Operarios_histrelevamientocupohoras_vactual_id_5d337dac_fk_Operarios_relevamientocupohoras_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientodet]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientodet_relevamientoCab_id_8d1974d9_fk_Operarios_relevamientocab_id] FOREIGN KEY([relevamientoCab_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientodet] CHECK CONSTRAINT [Operarios_histrelevamientodet_relevamientoCab_id_8d1974d9_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientodet]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientodet_tipoServPart_id_8c50e12e_fk_Operarios_tiposervicioparticular_id] FOREIGN KEY([tipoServPart_id])
REFERENCES [dbo].[Operarios_tiposervicioparticular] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientodet] CHECK CONSTRAINT [Operarios_histrelevamientodet_tipoServPart_id_8c50e12e_fk_Operarios_tiposervicioparticular_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientodet]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientodet_vactual_id_b70b316c_fk_Operarios_relevamientodet_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_relevamientodet] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientodet] CHECK CONSTRAINT [Operarios_histrelevamientodet_vactual_id_b70b316c_fk_Operarios_relevamientodet_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientoesp_perfil_id_1cfbcd8f_fk_Operarios_especializacion_id] FOREIGN KEY([perfil_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp] CHECK CONSTRAINT [Operarios_histrelevamientoesp_perfil_id_1cfbcd8f_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientoesp_relevamientoCab_id_fb961f58_fk_Operarios_relevamientocab_id] FOREIGN KEY([relevamientoCab_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp] CHECK CONSTRAINT [Operarios_histrelevamientoesp_relevamientoCab_id_fb961f58_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientoesp_tipo_id_887b9ce1_fk_Operarios_tiposervicio_id] FOREIGN KEY([tipo_id])
REFERENCES [dbo].[Operarios_tiposervicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp] CHECK CONSTRAINT [Operarios_histrelevamientoesp_tipo_id_887b9ce1_fk_Operarios_tiposervicio_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientoesp_tipoHora_id_f4a975be_fk_Operarios_tipohorario_id] FOREIGN KEY([tipoHora_id])
REFERENCES [dbo].[Operarios_tipohorario] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp] CHECK CONSTRAINT [Operarios_histrelevamientoesp_tipoHora_id_f4a975be_fk_Operarios_tipohorario_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientoesp_vactual_id_7f57a9df_fk_Operarios_relevamientoesp_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_relevamientoesp] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientoesp] CHECK CONSTRAINT [Operarios_histrelevamientoesp_vactual_id_7f57a9df_fk_Operarios_relevamientoesp_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientomensualeros]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientomensualeros_relevamientoCab_id_95d8fab7_fk_Operarios_relevamientocab_id] FOREIGN KEY([relevamientoCab_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientomensualeros] CHECK CONSTRAINT [Operarios_histrelevamientomensualeros_relevamientoCab_id_95d8fab7_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_histrelevamientomensualeros]  WITH CHECK ADD  CONSTRAINT [Operarios_histrelevamientomensualeros_vactual_id_d3fda2eb_fk_Operarios_relevamientomensualeros_id] FOREIGN KEY([vactual_id])
REFERENCES [dbo].[Operarios_relevamientomensualeros] ([id])
GO
ALTER TABLE [dbo].[Operarios_histrelevamientomensualeros] CHECK CONSTRAINT [Operarios_histrelevamientomensualeros_vactual_id_d3fda2eb_fk_Operarios_relevamientomensualeros_id]
GO
ALTER TABLE [dbo].[Operarios_horasnoprocesadas]  WITH CHECK ADD  CONSTRAINT [Operarios_horasnoprocesadas_puntoServicio_id_b6ed3cff_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_horasnoprocesadas] CHECK CONSTRAINT [Operarios_horasnoprocesadas_puntoServicio_id_b6ed3cff_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_horasprocesadas]  WITH CHECK ADD  CONSTRAINT [Operarios_horasprocesadas_asignacionDet_id_44d5940c_fk_Operarios_asignaciondet_id] FOREIGN KEY([asignacionDet_id])
REFERENCES [dbo].[Operarios_asignaciondet] ([id])
GO
ALTER TABLE [dbo].[Operarios_horasprocesadas] CHECK CONSTRAINT [Operarios_horasprocesadas_asignacionDet_id_44d5940c_fk_Operarios_asignaciondet_id]
GO
ALTER TABLE [dbo].[Operarios_horasprocesadas]  WITH CHECK ADD  CONSTRAINT [Operarios_horasprocesadas_puntoServicio_id_4d1d26e7_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_horasprocesadas] CHECK CONSTRAINT [Operarios_horasprocesadas_puntoServicio_id_4d1d26e7_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_notificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_notificacion_planificacionEsp_id_10104f73_fk_Operarios_planificacionesp_id] FOREIGN KEY([planificacionEsp_id])
REFERENCES [dbo].[Operarios_planificacionesp] ([id])
GO
ALTER TABLE [dbo].[Operarios_notificacion] CHECK CONSTRAINT [Operarios_notificacion_planificacionEsp_id_10104f73_fk_Operarios_planificacionesp_id]
GO
ALTER TABLE [dbo].[Operarios_notificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_notificacion_userFiscal_id_c599030d_fk_auth_user_id] FOREIGN KEY([userFiscal_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_notificacion] CHECK CONSTRAINT [Operarios_notificacion_userFiscal_id_c599030d_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_notificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_notificacion_userJefe_id_de28e74d_fk_auth_user_id] FOREIGN KEY([userJefe_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_notificacion] CHECK CONSTRAINT [Operarios_notificacion_userJefe_id_de28e74d_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_notificacion]  WITH CHECK ADD  CONSTRAINT [Operarios_notificacion_usuario_id_daa567ce_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_notificacion] CHECK CONSTRAINT [Operarios_notificacion_usuario_id_daa567ce_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_operario]  WITH CHECK ADD  CONSTRAINT [Operarios_operario_ciudad_id_524d1bab_fk_Operarios_ciudad_id] FOREIGN KEY([ciudad_id])
REFERENCES [dbo].[Operarios_ciudad] ([id])
GO
ALTER TABLE [dbo].[Operarios_operario] CHECK CONSTRAINT [Operarios_operario_ciudad_id_524d1bab_fk_Operarios_ciudad_id]
GO
ALTER TABLE [dbo].[Operarios_operario]  WITH CHECK ADD  CONSTRAINT [Operarios_operario_nacionalidad_id_c7ae4a38_fk_Operarios_nacionalidad_id] FOREIGN KEY([nacionalidad_id])
REFERENCES [dbo].[Operarios_nacionalidad] ([id])
GO
ALTER TABLE [dbo].[Operarios_operario] CHECK CONSTRAINT [Operarios_operario_nacionalidad_id_c7ae4a38_fk_Operarios_nacionalidad_id]
GO
ALTER TABLE [dbo].[Operarios_operario_profesion]  WITH CHECK ADD  CONSTRAINT [Operarios_operario_profesion_especializacion_id_8ddadee5_fk_Operarios_especializacion_id] FOREIGN KEY([especializacion_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_operario_profesion] CHECK CONSTRAINT [Operarios_operario_profesion_especializacion_id_8ddadee5_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_operario_profesion]  WITH CHECK ADD  CONSTRAINT [Operarios_operario_profesion_operario_id_9105700f_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_operario_profesion] CHECK CONSTRAINT [Operarios_operario_profesion_operario_id_9105700f_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_ordenserviciocab]  WITH CHECK ADD  CONSTRAINT [Operarios_ordenserviciocab_puntoServicio_id_35fab93e_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_ordenserviciocab] CHECK CONSTRAINT [Operarios_ordenserviciocab_puntoServicio_id_35fab93e_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_ordenserviciocab]  WITH CHECK ADD  CONSTRAINT [Operarios_ordenserviciocab_tipoOrden_id_91a65efd_fk_Operarios_tipoorden_id] FOREIGN KEY([tipoOrden_id])
REFERENCES [dbo].[Operarios_tipoorden] ([id])
GO
ALTER TABLE [dbo].[Operarios_ordenserviciocab] CHECK CONSTRAINT [Operarios_ordenserviciocab_tipoOrden_id_91a65efd_fk_Operarios_tipoorden_id]
GO
ALTER TABLE [dbo].[Operarios_ordenserviciocab]  WITH CHECK ADD  CONSTRAINT [Operarios_ordenserviciocab_usuario_id_0231520c_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_ordenserviciocab] CHECK CONSTRAINT [Operarios_ordenserviciocab_usuario_id_0231520c_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_ordenserviciodet]  WITH CHECK ADD  CONSTRAINT [Operarios_ordenserviciodet_operario_id_3c357a6b_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_ordenserviciodet] CHECK CONSTRAINT [Operarios_ordenserviciodet_operario_id_3c357a6b_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_ordenserviciodet]  WITH CHECK ADD  CONSTRAINT [Operarios_ordenserviciodet_ordenServicioCab_id_ca1f5cce_fk_Operarios_ordenserviciocab_id] FOREIGN KEY([ordenServicioCab_id])
REFERENCES [dbo].[Operarios_ordenserviciocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_ordenserviciodet] CHECK CONSTRAINT [Operarios_ordenserviciodet_ordenServicioCab_id_ca1f5cce_fk_Operarios_ordenserviciocab_id]
GO
ALTER TABLE [dbo].[Operarios_ordenserviciodet]  WITH CHECK ADD  CONSTRAINT [Operarios_ordenserviciodet_usuario_id_2079e8a2_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_ordenserviciodet] CHECK CONSTRAINT [Operarios_ordenserviciodet_usuario_id_2079e8a2_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_planificacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_planificacioncab_puntoServicio_id_b1236663_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_planificacioncab] CHECK CONSTRAINT [Operarios_planificacioncab_puntoServicio_id_b1236663_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_planificacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_planificacioncab_usuario_id_616c533d_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_planificacioncab] CHECK CONSTRAINT [Operarios_planificacioncab_usuario_id_616c533d_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_planificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_planificacionesp_especialista_id_cb13f68a_fk_Operarios_especializacion_id] FOREIGN KEY([especialista_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_planificacionesp] CHECK CONSTRAINT [Operarios_planificacionesp_especialista_id_cb13f68a_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_planificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_planificacionesp_planificacionCab_id_a4b771c2_fk_Operarios_planificacioncab_id] FOREIGN KEY([planificacionCab_id])
REFERENCES [dbo].[Operarios_planificacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_planificacionesp] CHECK CONSTRAINT [Operarios_planificacionesp_planificacionCab_id_a4b771c2_fk_Operarios_planificacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_planificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_planificacionesp_tipo_id_14563a29_fk_Operarios_tiposervicio_id] FOREIGN KEY([tipo_id])
REFERENCES [dbo].[Operarios_tiposervicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_planificacionesp] CHECK CONSTRAINT [Operarios_planificacionesp_tipo_id_14563a29_fk_Operarios_tiposervicio_id]
GO
ALTER TABLE [dbo].[Operarios_planificacionesp]  WITH CHECK ADD  CONSTRAINT [Operarios_planificacionesp_tipoHora_id_6961c0c4_fk_Operarios_tipohorario_id] FOREIGN KEY([tipoHora_id])
REFERENCES [dbo].[Operarios_tipohorario] ([id])
GO
ALTER TABLE [dbo].[Operarios_planificacionesp] CHECK CONSTRAINT [Operarios_planificacionesp_tipoHora_id_6961c0c4_fk_Operarios_tipohorario_id]
GO
ALTER TABLE [dbo].[Operarios_planificacionope]  WITH CHECK ADD  CONSTRAINT [Operarios_planificacionope_especialista_id_6a66a292_fk_Operarios_especializacion_id] FOREIGN KEY([especialista_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_planificacionope] CHECK CONSTRAINT [Operarios_planificacionope_especialista_id_6a66a292_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_planificacionope]  WITH CHECK ADD  CONSTRAINT [Operarios_planificacionope_planificacionCab_id_765d6aac_fk_Operarios_planificacioncab_id] FOREIGN KEY([planificacionCab_id])
REFERENCES [dbo].[Operarios_planificacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_planificacionope] CHECK CONSTRAINT [Operarios_planificacionope_planificacionCab_id_765d6aac_fk_Operarios_planificacioncab_id]
GO
ALTER TABLE [dbo].[Operarios_procesosincronizacion]  WITH CHECK ADD  CONSTRAINT [Operarios_procesosincronizacion_usuario_id_b7d34d56_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_procesosincronizacion] CHECK CONSTRAINT [Operarios_procesosincronizacion_usuario_id_b7d34d56_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_puntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_puntoservicio_Ciudad_id_9c838729_fk_Operarios_ciudad_id] FOREIGN KEY([Ciudad_id])
REFERENCES [dbo].[Operarios_ciudad] ([id])
GO
ALTER TABLE [dbo].[Operarios_puntoservicio] CHECK CONSTRAINT [Operarios_puntoservicio_Ciudad_id_9c838729_fk_Operarios_ciudad_id]
GO
ALTER TABLE [dbo].[Operarios_puntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_puntoservicio_Cliente_id_4afd61b9_fk_Operarios_cliente_id] FOREIGN KEY([Cliente_id])
REFERENCES [dbo].[Operarios_cliente] ([id])
GO
ALTER TABLE [dbo].[Operarios_puntoservicio] CHECK CONSTRAINT [Operarios_puntoservicio_Cliente_id_4afd61b9_fk_Operarios_cliente_id]
GO
ALTER TABLE [dbo].[Operarios_puntoservicio]  WITH CHECK ADD  CONSTRAINT [Operarios_puntoservicio_usuario_id_2e325542_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_puntoservicio] CHECK CONSTRAINT [Operarios_puntoservicio_usuario_id_2e325542_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientocab]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientocab_puntoServicio_id_b6c8a4bd_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientocab] CHECK CONSTRAINT [Operarios_relevamientocab_puntoServicio_id_b6c8a4bd_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientocab]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientocab_tipoSalario_id_c6e78c7e_fk_Operarios_tiposalario_id] FOREIGN KEY([tipoSalario_id])
REFERENCES [dbo].[Operarios_tiposalario] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientocab] CHECK CONSTRAINT [Operarios_relevamientocab_tipoSalario_id_c6e78c7e_fk_Operarios_tiposalario_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientocab]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientocab_usuario_id_2446c0fd_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientocab] CHECK CONSTRAINT [Operarios_relevamientocab_usuario_id_2446c0fd_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientocupohoras]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientocupohoras_relevamientoCab_id_f322ded2_fk_Operarios_relevamientocab_id] FOREIGN KEY([relevamientoCab_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientocupohoras] CHECK CONSTRAINT [Operarios_relevamientocupohoras_relevamientoCab_id_f322ded2_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientocupohoras]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientocupohoras_tipoHora_id_de2c9f83_fk_Operarios_tipohorario_id] FOREIGN KEY([tipoHora_id])
REFERENCES [dbo].[Operarios_tipohorario] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientocupohoras] CHECK CONSTRAINT [Operarios_relevamientocupohoras_tipoHora_id_de2c9f83_fk_Operarios_tipohorario_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientodet]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientodet_relevamientoCab_id_539233bb_fk_Operarios_relevamientocab_id] FOREIGN KEY([relevamientoCab_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientodet] CHECK CONSTRAINT [Operarios_relevamientodet_relevamientoCab_id_539233bb_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientodet]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientodet_tipoServPart_id_8925b48a_fk_Operarios_tiposervicioparticular_id] FOREIGN KEY([tipoServPart_id])
REFERENCES [dbo].[Operarios_tiposervicioparticular] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientodet] CHECK CONSTRAINT [Operarios_relevamientodet_tipoServPart_id_8925b48a_fk_Operarios_tiposervicioparticular_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientoesp_perfil_id_4b36d4c6_fk_Operarios_especializacion_id] FOREIGN KEY([perfil_id])
REFERENCES [dbo].[Operarios_especializacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientoesp] CHECK CONSTRAINT [Operarios_relevamientoesp_perfil_id_4b36d4c6_fk_Operarios_especializacion_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientoesp_relevamientoCab_id_1e4af028_fk_Operarios_relevamientocab_id] FOREIGN KEY([relevamientoCab_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientoesp] CHECK CONSTRAINT [Operarios_relevamientoesp_relevamientoCab_id_1e4af028_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientoesp_tipo_id_5b5fcddc_fk_Operarios_tiposervicio_id] FOREIGN KEY([tipo_id])
REFERENCES [dbo].[Operarios_tiposervicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientoesp] CHECK CONSTRAINT [Operarios_relevamientoesp_tipo_id_5b5fcddc_fk_Operarios_tiposervicio_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientoesp]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientoesp_tipoHora_id_56566f41_fk_Operarios_tipohorario_id] FOREIGN KEY([tipoHora_id])
REFERENCES [dbo].[Operarios_tipohorario] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientoesp] CHECK CONSTRAINT [Operarios_relevamientoesp_tipoHora_id_56566f41_fk_Operarios_tipohorario_id]
GO
ALTER TABLE [dbo].[Operarios_relevamientomensualeros]  WITH CHECK ADD  CONSTRAINT [Operarios_relevamientomensualeros_relevamientoCab_id_ea21e1fb_fk_Operarios_relevamientocab_id] FOREIGN KEY([relevamientoCab_id])
REFERENCES [dbo].[Operarios_relevamientocab] ([id])
GO
ALTER TABLE [dbo].[Operarios_relevamientomensualeros] CHECK CONSTRAINT [Operarios_relevamientomensualeros_relevamientoCab_id_ea21e1fb_fk_Operarios_relevamientocab_id]
GO
ALTER TABLE [dbo].[Operarios_remplazomanresp]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazomanresp_id_reemplazo_id_63b96b24_fk_Operarios_remplazoscab_id] FOREIGN KEY([id_reemplazo_id])
REFERENCES [dbo].[Operarios_remplazoscab] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazomanresp] CHECK CONSTRAINT [Operarios_remplazomanresp_id_reemplazo_id_63b96b24_fk_Operarios_remplazoscab_id]
GO
ALTER TABLE [dbo].[Operarios_remplazomanresp]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazomanresp_motivo_id_0b3f7cb9_fk_Operarios_motivos_id] FOREIGN KEY([motivo_id])
REFERENCES [dbo].[Operarios_motivos] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazomanresp] CHECK CONSTRAINT [Operarios_remplazomanresp_motivo_id_0b3f7cb9_fk_Operarios_motivos_id]
GO
ALTER TABLE [dbo].[Operarios_remplazomanresp]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazomanresp_usuario_id_fd793278_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazomanresp] CHECK CONSTRAINT [Operarios_remplazomanresp_usuario_id_fd793278_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_remplazoscab]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazoscab_alertaId_id_cbd2429c_fk_Operarios_alertas_id] FOREIGN KEY([alertaId_id])
REFERENCES [dbo].[Operarios_alertas] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazoscab] CHECK CONSTRAINT [Operarios_remplazoscab_alertaId_id_cbd2429c_fk_Operarios_alertas_id]
GO
ALTER TABLE [dbo].[Operarios_remplazoscab]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazoscab_operario_id_3ce612b3_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazoscab] CHECK CONSTRAINT [Operarios_remplazoscab_operario_id_3ce612b3_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_remplazoscab]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazoscab_usuario_id_460aa830_fk_auth_user_id] FOREIGN KEY([usuario_id])
REFERENCES [dbo].[auth_user] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazoscab] CHECK CONSTRAINT [Operarios_remplazoscab_usuario_id_460aa830_fk_auth_user_id]
GO
ALTER TABLE [dbo].[Operarios_remplazosdet]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazosdet_Asignacion_id_87957848_fk_Operarios_asignaciondet_id] FOREIGN KEY([Asignacion_id])
REFERENCES [dbo].[Operarios_asignaciondet] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazosdet] CHECK CONSTRAINT [Operarios_remplazosdet_Asignacion_id_87957848_fk_Operarios_asignaciondet_id]
GO
ALTER TABLE [dbo].[Operarios_remplazosdet]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazosdet_puntoServicio_id_cac53a77_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazosdet] CHECK CONSTRAINT [Operarios_remplazosdet_puntoServicio_id_cac53a77_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_remplazosdet]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazosdet_remplazo_id_1800a48c_fk_Operarios_operario_id] FOREIGN KEY([remplazo_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazosdet] CHECK CONSTRAINT [Operarios_remplazosdet_remplazo_id_1800a48c_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_remplazosdet]  WITH CHECK ADD  CONSTRAINT [Operarios_remplazosdet_remplazoCab_id_cf41ccfb_fk_Operarios_remplazoscab_id] FOREIGN KEY([remplazoCab_id])
REFERENCES [dbo].[Operarios_remplazoscab] ([id])
GO
ALTER TABLE [dbo].[Operarios_remplazosdet] CHECK CONSTRAINT [Operarios_remplazosdet_remplazoCab_id_cf41ccfb_fk_Operarios_remplazoscab_id]
GO
ALTER TABLE [dbo].[Operarios_sincronizacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_sincronizacioncab_operario_id_02fa02aa_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_sincronizacioncab] CHECK CONSTRAINT [Operarios_sincronizacioncab_operario_id_02fa02aa_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_sincronizacioncab]  WITH CHECK ADD  CONSTRAINT [Operarios_sincronizacioncab_proceso_id_d347f6e2_fk_Operarios_procesosincronizacion_id] FOREIGN KEY([proceso_id])
REFERENCES [dbo].[Operarios_procesosincronizacion] ([id])
GO
ALTER TABLE [dbo].[Operarios_sincronizacioncab] CHECK CONSTRAINT [Operarios_sincronizacioncab_proceso_id_d347f6e2_fk_Operarios_procesosincronizacion_id]
GO
ALTER TABLE [dbo].[Operarios_sincronizaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_sincronizaciondet_operario_id_d91356a8_fk_Operarios_operario_id] FOREIGN KEY([operario_id])
REFERENCES [dbo].[Operarios_operario] ([id])
GO
ALTER TABLE [dbo].[Operarios_sincronizaciondet] CHECK CONSTRAINT [Operarios_sincronizaciondet_operario_id_d91356a8_fk_Operarios_operario_id]
GO
ALTER TABLE [dbo].[Operarios_sincronizaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_sincronizaciondet_puntoServicio_id_3f3e0384_fk_Operarios_puntoservicio_id] FOREIGN KEY([puntoServicio_id])
REFERENCES [dbo].[Operarios_puntoservicio] ([id])
GO
ALTER TABLE [dbo].[Operarios_sincronizaciondet] CHECK CONSTRAINT [Operarios_sincronizaciondet_puntoServicio_id_3f3e0384_fk_Operarios_puntoservicio_id]
GO
ALTER TABLE [dbo].[Operarios_sincronizaciondet]  WITH CHECK ADD  CONSTRAINT [Operarios_sincronizaciondet_sincronizacionCab_id_888d19d9_fk_Operarios_sincronizacioncab_id] FOREIGN KEY([sincronizacionCab_id])
REFERENCES [dbo].[Operarios_sincronizacioncab] ([id])
GO
ALTER TABLE [dbo].[Operarios_sincronizaciondet] CHECK CONSTRAINT [Operarios_sincronizaciondet_sincronizacionCab_id_888d19d9_fk_Operarios_sincronizacioncab_id]
GO
ALTER TABLE [dbo].[django_admin_log]  WITH NOCHECK ADD  CONSTRAINT [django_admin_log_action_flag_a8637d59_check] CHECK  (([action_flag]>=(0)))
GO
ALTER TABLE [dbo].[django_admin_log] CHECK CONSTRAINT [django_admin_log_action_flag_a8637d59_check]
GO
/****** Object:  StoredProcedure [dbo].[activacion_puntoServicio]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE   PROCEDURE [dbo].[activacion_puntoServicio]   
  

	@p_id int,
	@p_activo bit,
	@p_usuario int,
	@p_comentario nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	BEGIN TRAN @TransactionName 
	BEGIN TRY
	
		DECLARE @tmp1_vregistro int;
		DECLARE @nuevoID int;
		DECLARE @p_vregistro int;
		Declare @fechaCambio datetime;

		SET @fechaCambio=CURRENT_TIMESTAMP;

		/* 1 - Punto de Servicio*/
				
				select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histpuntoservicio where vactual_id=@p_id;
				if @tmp1_vregistro is NULL
				begin
					set @tmp1_vregistro=1;
					INSERT INTO [dbo].[Operarios_histpuntoservicio]
					   ([CodPuntoServicio],[NombrePServicio],[DireccionContrato]
					   ,[Barrios],[Contacto],[MailContacto]
					   ,[TelefonoContacto],[Coordenadas],[NumeroMarcador]
					   ,[vfechaInicio],[vfechaFin],[vregistro]
					   ,[Ciudad_id],[Cliente_id],[vactual_id],activo,comentario,usuario_id)
					SELECT 
						[CodPuntoServicio],[NombrePServicio],[DireccionContrato],
						[Barrios],[Contacto],[MailContacto],
						[TelefonoContacto],[Coordenadas],[NumeroMarcador],
						@fechaCambio,NULL,1,
						[Ciudad_id],[Cliente_id],@p_id,activo,comentario,usuario_id
						from dbo.Operarios_puntoservicio where id=@p_id;
				end

				update dbo.Operarios_histpuntoservicio set vfechaFin=@fechaCambio where vactual_id=@p_id;

				update dbo.Operarios_puntoservicio set
					activo=@p_activo,
					comentario=@p_comentario,
					usuario_id=@p_usuario
					where id=@p_id;

				INSERT INTO dbo.Operarios_histpuntoservicio (CodPuntoServicio,NombrePServicio,DireccionContrato,Barrios,Contacto,MailContacto,TelefonoContacto,Coordenadas,Ciudad_id,Cliente_id,NumeroMarcador,vfechaInicio,vfechaFin,vregistro,vactual_id,activo,comentario,usuario_id)
				select CodPuntoServicio,NombrePServicio,DireccionContrato,Barrios,Contacto,MailContacto,
				TelefonoContacto,Coordenadas,Ciudad_id,Cliente_id,NumeroMarcador,@fechaCambio,NULL,@tmp1_vregistro+1,
				@p_id,activo,comentario,usuario_id from dbo.Operarios_puntoservicio where id=@p_id;

			COMMIT TRANSACTION @TransactionName;
			SET @retorno=0;
	END TRY 
	BEGIN CATCH 
		print error_message();
		SELECT ERROR_MESSAGE() AS ErrorMessage
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;

	END CATCH

	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[actividad_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE         PROCEDURE [dbo].[actividad_manager]   
	@json_cab nvarchar(max),
	@json_det nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		DECLARE @hrm0_id int;
		DECLARE @hrm0_lunEnt time;
		DECLARE @hrm0_lunSal time;
		DECLARE @hrm0_marEnt time;
		DECLARE @hrm0_marSal time;
		DECLARE @hrm0_mieEnt time;
		DECLARE @hrm0_mieSal time;
		DECLARE @hrm0_jueEnt time;
		DECLARE @hrm0_jueSal time;
		DECLARE @hrm0_vieEnt time;
		DECLARE @hrm0_vieSal time;
		DECLARE @hrm0_sabEnt time;
		DECLARE @hrm0_sabSal time;
		DECLARE @hrm0_domEnt time;
		DECLARE @hrm0_domSal time;
		DECLARE @hrm0_actividadCab_id int;
		DECLARE @hrm0_operario_id int;
		DECLARE @hrm0_fechaInicio date;
		DECLARE @hrm0_totalHoras nvarchar(max);
		DECLARE @hrm0_numTotalHoras int
		DECLARE @hrm0_fechaFin date;
		DECLARE @hrm0_supervisor bit;
		DECLARE @hrm0_perfil_id int;
		declare @tmp1_vregistro int;
		DECLARE @hrm0_eliminado nvarchar(max);
		SET @fechaCambio=CURRENT_TIMESTAMP;
		DECLARE @RC int;
		DECLARE @tmp nvarchar(max);
			--select 'entrare en cabecera'
			EXECUTE @RC = [dbo].[actividadcab_trg] @json_cab,@fechaCambio,@retorno
			--select 'salid de cabecera'
			--SELECT "value" FROM OpenJson(@json_det);
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_det)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					--insert into infolog(fechaHora,info) values(@fechaCambio,@tmp);			
					EXECUTE @RC = [dbo].[actividaddet_trg] @tmp,@fechaCambio,@retorno
				end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt

		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		SET @retorno=1;
		ROLLBACK TRAN @TransactionName; 
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_det);
		Select 1 as resultado;
		RETURN 1;
	END CATCH
	Select 0 as resultado;
	RETURN 0;

END	

GO
/****** Object:  StoredProcedure [dbo].[actividadcab_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE         PROCEDURE [dbo].[actividadcab_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_usuario_id int;
		DECLARE @p_planificacionEsp_id int;
		DECLARE @p_totalasignado nvarchar(max);
		DECLARE @p_numTotalasignado int;
		DECLARE @p_fechaUltimaMod datetime2 ;
		DECLARE @p_id int;
		DECLARE @superaHora bit;

		select @p_usuario_id="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
		select @p_planificacionEsp_id="value" from OpenJson(@json) where "key"='planificacionEsp_id' and "value"!='None';
		select @p_totalasignado="value" from OpenJson(@json) where "key"='totalasignado' and "value"!='None';
		select @p_numTotalasignado="value" from OpenJson(@json) where "key"='numTotalAsignado' and "value"!='None';
		select @p_fechaUltimaMod=convert(datetime,"value",20) from OpenJson(@json) where "key"='fechaUltimaMod' and  "value"!='None' and "value"!='00';
		
		
		--select 'termine de castear';
		if @p_fechaUltimaMod is NULL
		begin
			set @p_fechaUltimaMod = CURRENT_TIMESTAMP
		end

		select @p_id=cast("value" as int) from OpenJson(@json) where "key"='id' and "value"!='None';
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histactividadcab where vactual_id=@p_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histactividadcab(usuario_id,planificacionEsp_id,totalasignado,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,reAsignar,numTotalAsignado)
				select usuario_id,planificacionEsp_id,totalasignado,fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,'False',numTotalasignado from dbo.Operarios_actividadcab where id=@p_id;
			end
			update dbo.Operarios_histactividadcab set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro;
			set @tmp1_vregistro=@tmp1_vregistro+1;
			INSERT INTO dbo.Operarios_histactividadcab(usuario_id,planificacionEsp_id,totalasignado,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,reAsignar,numTotalAsignado)
			select @p_usuario_id,@p_planificacionEsp_id,@p_totalasignado,@p_fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,'False',@p_numTotalasignado
			update dbo.Operarios_actividadcab set 
				 usuario_id=@p_usuario_id,planificacionEsp_id=@p_planificacionEsp_id,totalasignado=@p_totalasignado,fechaUltimaMod=@p_fechaUltimaMod,numTotalAsignado=@p_numTotalasignado where id=@p_id;
		end
		if  @p_id is NULL
		begin
			set @tmp1_vregistro=1;
			INSERT INTO dbo.Operarios_actividadcab(usuario_id,planificacionEsp_id,totalasignado,fechaUltimaMod,numTotalAsignado)
			select @p_usuario_id,@p_planificacionEsp_id,@p_totalasignado,@p_fechaUltimaMod,@p_numTotalasignado;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histactividadcab(usuario_id,planificacionEsp_id,totalasignado,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalAsignado)
			select @p_usuario_id,@p_planificacionEsp_id,@p_totalasignado,@p_fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotalasignado
		end

		
		update dbo.Operarios_planificacionesp set estado='PGR'
		where id=@p_planificacionEsp_id and @p_planificacionEsp_id is not NULL;

		update dbo.Operarios_planificacionesp set estado='FIN'
		where id=@p_planificacionEsp_id and @p_planificacionEsp_id is not NULL and
		numCantHoras<=(select sum(numTotalAsignado) from dbo.Operarios_actividadcab where planificacionEsp_id=@p_planificacionEsp_id)

		SET @retorno=0;
		return 0;
END
GO
/****** Object:  StoredProcedure [dbo].[actividaddet_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE         PROCEDURE [dbo].[actividaddet_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		--SELECT @json;
		--insert into dbo.infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@json);
		--insert into dbo.infolog(fechaHora,info) values(CURRENT_TIMESTAMP,'entre en datelle');
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @area nvarchar(50);
		DECLARE @sector nvarchar(50);
		DECLARE @p_totalHoras nvarchar(max);		
		DECLARE @p_supervisor bit;
		DECLARE @p_domSal time;
		DECLARE @p_domEnt time;
		DECLARE @p_sabSal time;
		DECLARE @p_sabEnt time;
		DECLARE @p_vieSal time;
		DECLARE @p_vieEnt time;
		DECLARE @p_jueSal time;
		DECLARE @p_jueEnt time;
		DECLARE @p_mieSal time;
		DECLARE @p_mieEnt time;
		DECLARE @p_marSal time;
		DECLARE @p_marEnt time;
		DECLARE @p_lunSal time;
		DECLARE @p_lunEnt time;
		DECLARE @p_id int;
		DECLARE @p_perfil_id int;
		DECLARE @cantidad int;
		DECLARE @p_operario_id int;
		DECLARE @p_actividadCab_id int;
		DECLARE @p_numTotalHoras int;
		

 		select @p_perfil_id=cast("value" as int) from OpenJson(@json) where "key"='perfil_id' and "value"!='None';
		select @cantidad=cast("value" as int) from OpenJson(@json) where "key"='cantidad' and "value"!='None';
		select @p_numTotalHoras=cast("value" as int) from OpenJson(@json) where "key"='numTotalHoras' and "value"!='None' and "value"!='00';
		select @p_operario_id=cast("value" as int) from OpenJson(@json) where "key"='operario_id' and "value"!='None';
		select @p_actividadCab_id=cast("value" as int) from OpenJson(@json) where "key"='actividadCab_id' and "value"!='None';
		select @p_supervisor="value" from OpenJson(@json) where "key"='supervisor';
		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @area="value" from OpenJson(@json) where "key"='area';
		select @sector="value" from OpenJson(@json) where "key"='sector';
		select @p_totalHoras="value" from OpenJson(@json) where "key"='totalHoras' and "value"!='None' and "value"!='00';
		select @p_fechaInicio=convert(date,"value", 105) from OpenJson(@json) where "key"='fechaInicio' and "value"!='None';
		select @p_fechaFin=convert(date,"value", 105) from OpenJson(@json) where "key"='fechaFin' and "value"!='None';	
		select @p_domSal=cast("value" as time) from OpenJson(@json) where "key"='domSal' and "value"!='None';
		select @p_domEnt=cast("value" as time) from OpenJson(@json) where "key"='domEnt' and "value"!='None';
		select @p_sabSal=cast("value" as time) from OpenJson(@json) where "key"='sabSal' and "value"!='None';
		select @p_sabEnt=cast("value" as time) from OpenJson(@json) where "key"='sabEnt' and "value"!='None';
		select @p_vieSal=cast("value" as time) from OpenJson(@json) where "key"='vieSal' and "value"!='None';
		select @p_vieEnt=cast("value" as time) from OpenJson(@json) where "key"='vieEnt' and "value"!='None';
		select @p_jueSal=cast("value" as time) from OpenJson(@json) where "key"='jueSal' and "value"!='None';
		select @p_jueEnt=cast("value" as time) from OpenJson(@json) where "key"='jueEnt' and "value"!='None';
		select @p_mieSal=cast("value" as time) from OpenJson(@json) where "key"='mieSal' and "value"!='None';
		select @p_mieEnt=cast("value" as time) from OpenJson(@json) where "key"='mieEnt' and "value"!='None';
		select @p_marSal=cast("value" as time) from OpenJson(@json) where "key"='marSal' and "value"!='None';
		select @p_marEnt=cast("value" as time) from OpenJson(@json) where "key"='marEnt' and "value"!='None';
		select @p_lunSal=cast("value" as time) from OpenJson(@json) where "key"='lunSal' and "value"!='None';
		select @p_lunEnt=cast("value" as time) from OpenJson(@json) where "key"='lunEnt' and "value"!='None';
		select @p_id="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histactividadcab where vactual_id=@p_actividadCab_id
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histactividaddet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,actividadCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalHoras,eliminado,area,sector,cantidad)
				select perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,actividadCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotalHoras,'False',@area,@sector,@cantidad from dbo.Operarios_actividaddet where id=@p_id;
			end
			update dbo.Operarios_histactividaddet set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				INSERT INTO dbo.Operarios_histactividaddet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,actividadCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalHoras,eliminado,area,sector,cantidad)
				select @p_perfil_id,@p_supervisor,@p_fechaFin,@p_totalHoras,@p_fechaInicio,@p_operario_id,@p_actividadCab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotalHoras,'False',@area,@sector,@cantidad
				update dbo.Operarios_actividaddet set 
					 perfil_id=@p_perfil_id,supervisor=@p_supervisor,fechaFin=@p_fechaFin,totalHoras=@p_totalHoras,fechaInicio=@p_fechaInicio,operario_id=@p_operario_id,actividadCab_id=@p_actividadCab_id,domSal=@p_domSal,domEnt=@p_domEnt,sabSal=@p_sabSal,sabEnt=@p_sabEnt,vieSal=@p_vieSal,vieEnt=@p_vieEnt,jueSal=@p_jueSal,jueEnt=@p_jueEnt,mieSal=@p_mieSal,
					 area=@area,sector=@sector,cantidad=@cantidad,
					 mieEnt=@p_mieEnt,marSal=@p_marSal,marEnt=@p_marEnt,lunSal=@p_lunSal,lunEnt=@p_lunEnt,numTotalHoras=@p_numTotalHoras where id=@p_id;
			end

			/*if @delete is not NULL and @delete='True'
			begin
                update Operarios_histactividaddet set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_actividaddet  where id=@p_id;
			end*/

			

		end
		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histactividadcab where vactual_id=@p_actividadCab_id;
			INSERT INTO dbo.Operarios_actividaddet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,actividadCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,numTotalHoras,eliminado,area,sector,cantidad)
			select @p_perfil_id,@p_supervisor,@p_fechaFin,@p_totalHoras,@p_fechaInicio,@p_operario_id,@p_actividadCab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@p_numTotalHoras,'False',@area,@sector,@cantidad;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histactividaddet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,actividadCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalHoras,eliminado,area,sector,cantidad)
			select @p_perfil_id,@p_supervisor,@p_fechaFin,@p_totalHoras,@p_fechaInicio,@p_operario_id,@p_actividadCab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotalHoras,'False',@area,@sector,@cantidad
		end
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[alertasave_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[alertasave_trg]   
	@json nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
		SET NOCOUNT ON;
		DECLARE @p_id int;
		declare @p_accion nvarchar(max);
		declare @p_hora time;
		declare @p_motivo_id int;
		declare @p_fechaRetorno datetime;
		declare @p_comentarios nvarchar(max);
		declare @p_escalado bit;
		declare @p_id_alerta_id int;
		declare @p_usuario_id int;
		declare @p_id_reemplazo_id int;
		declare @p_fecha_creacion datetime2;

		
		Select @p_id ="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		select @p_accion ="value" from OpenJson(@json) where "key"='accion' and "value"!='None';
		select @p_hora ="value" from OpenJson(@json) where "key"='hora' and "value"!='None';
		select @p_motivo_id ="value" from OpenJson(@json) where "key"='motivo_id' and "value"!='None';
		select @p_fechaRetorno =convert(datetime,"value",120) from OpenJson(@json) where "key"='fechaRetorno' and "value"!='None';
		select @p_comentarios ="value" from OpenJson(@json) where "key"='comentarios' and "value"!='None';
		select @p_escalado ="value" from OpenJson(@json) where "key"='escalado' and "value"!='None';
		select @p_id_alerta_id ="value" from OpenJson(@json) where "key"='alertaId_id' and "value"!='None';
		select @p_usuario_id ="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
		select @p_id_reemplazo_id ="value" from OpenJson(@json) where "key"='reemplazo_id' and "value"!='None';
		set @p_fecha_creacion = CURRENT_TIMESTAMP
		
		UPDATE dbo.Operarios_alertas set
			Estado='CERRADA'
		where id=@p_id_alerta_id;
		UPDATE [dbo].[Operarios_alertaresp]
		   SET [motivo_id] = @p_motivo_id,
				hora = cast(@p_fechaRetorno as time),
			  [fechaRetorno] = @p_fechaRetorno
			  ,[comentarios] = @p_comentarios
				WHERE id_alerta_id =@p_id_alerta_id;
		insert into dbo.Operarios_alertaresp(accion,motivo_id,
		fechaRetorno,hora,fecha_creacion,id_reemplazo_id,comentarios,escalado,id_alerta_id,usuario_id) select 
		'REEMPLAZO',@p_motivo_id,@p_fechaRetorno,@p_fechaRetorno,CURRENT_TIMESTAMP,@p_id_reemplazo_id,@p_comentarios,'False',@p_id_alerta_id,@p_usuario_id
		where  not exists(select id from dbo.Operarios_alertaresp where id_alerta_id=@p_id_alerta_id and accion='REEMPLAZO');
		

		SET @retorno=0;
		
END
GO
/****** Object:  StoredProcedure [dbo].[asig_jefeyfiscal_trigger]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[asig_jefeyfiscal_trigger]   
  

	@p_userJefe_id int,
	@p_userFiscal_id int,
	@veregistro int,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
	SET NOCOUNT ON;
	Declare @error nvarchar(max);
	declare @nuevoId int;
	DECLARE @TransactionName varchar(20) = 'Transactional';
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		 INSERT INTO [dbo].[Operarios_asigjefefiscal]([userFiscal_id],[userJefe_id])
		 select @p_userFiscal_id,@p_userJefe_id where not exists(select * from
		 dbo.Operarios_asigjefefiscal where userFiscal_id=@p_userFiscal_id and userJefe_id=@p_userJefe_id)
		 set @nuevoId=SCOPE_IDENTITY();
		 select @veregistro=max(vregistro) from dbo.Operarios_histasigjefefiscal where userFiscal_id=@p_userFiscal_id and userJefe_id=@p_userJefe_id;
		 if @veregistro is NUll
		 begin
			set @veregistro=0;
		 end
		 INSERT INTO [dbo].[Operarios_histasigjefefiscal]([userFiscal_id],[userJefe_id],[vfechaFin],[vfechaInicio],[vregistro],vactual_id)
		 values( @p_userFiscal_id,@p_userJefe_id,NULL,CURRENT_TIMESTAMP,@veregistro+1,@nuevoId); 
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH 
		set @error=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@error)
	END CATCH

	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[asig_psfiscal_trigger]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE        PROCEDURE [dbo].[asig_psfiscal_trigger]   
  

	@p_userFiscal_id int,
	@p_puntoServ_id int,
	@veregistro int,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
	SET NOCOUNT ON;
	Declare @error nvarchar(max);
	declare @nuevoId int;
	DECLARE @TransactionName varchar(20) = 'Transactional';
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		 INSERT INTO [dbo].[Operarios_asigfiscalpuntoservicio](puntoServicio_id,userFiscal_id)
		 select @p_puntoServ_id,@p_userFiscal_id where not exists(select * from
		 dbo.Operarios_asigfiscalpuntoservicio where userFiscal_id=@p_userFiscal_id and puntoServicio_id=@p_puntoServ_id)
		 set @nuevoId=SCOPE_IDENTITY();
		 select @veregistro=max(vregistro) from dbo.Operarios_histasigfiscalpuntoservicio where userFiscal_id=@p_userFiscal_id and puntoServicio_id=@p_puntoServ_id;
		 if @veregistro is NUll
		 begin
			set @veregistro=0;
		 end
		 set @veregistro=@veregistro+1;
		 INSERT INTO [dbo].[Operarios_histasigfiscalpuntoservicio](puntoServicio_id,userFiscal_id,[vfechaFin],[vfechaInicio],[vregistro],vactual_id)
		 values( @p_puntoServ_id,@p_userFiscal_id,NULL,CURRENT_TIMESTAMP,@veregistro,@nuevoId); 
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH 
		set @error=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@error)
	END CATCH

	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[asigfiscalpuntoservicio_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[asigfiscalpuntoservicio_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_userFiscal_id int;
		DECLARE @p_puntoServicio_id int;
		DECLARE @p_id int;

		select @p_userFiscal_id="value" from OpenJson(@json) where "key"='userFiscal_id';
		select @p_puntoServicio_id="value" from OpenJson(@json) where "key"='puntoServicio_id';
		select @p_id="value" from OpenJson(@json) where "key"='id';
		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histasigfiscalpuntoservicio where vactual_id=@p_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histasigfiscalpuntoservicio(userFiscal_id,puntoServicio_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
				select userFiscal_id,puntoServicio_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id from dbo.Operarios_asigfiscalpuntoservicio where id=@p_id;
			end
			update dbo.Operarios_histasigfiscalpuntoservicio set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro;
			set @tmp1_vregistro=@tmp1_vregistro+1;
			INSERT INTO dbo.Operarios_histasigfiscalpuntoservicio(userFiscal_id,puntoServicio_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
			select @p_userFiscal_id,@p_puntoServicio_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id
			update dbo.Operarios_asigfiscalpuntoservicio set 
				 userFiscal_id=@p_userFiscal_id,puntoServicio_id=@p_puntoServicio_id where id=@p_id;
		end
		if  @p_id is NULL
		begin
			set @tmp1_vregistro=1;
			INSERT INTO dbo.Operarios_asigfiscalpuntoservicio(userFiscal_id,puntoServicio_id)
			select @p_userFiscal_id,@p_puntoServicio_id;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histasigfiscalpuntoservicio(userFiscal_id,puntoServicio_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
			select @p_userFiscal_id,@p_puntoServicio_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id
		end
		SET @retorno=0;
		Select @retorno as resultado;
END


GO
/****** Object:  StoredProcedure [dbo].[asigjefefisc_des_trigger]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE        PROCEDURE [dbo].[asigjefefisc_des_trigger]   
  

	@p_userJefe_id int,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;
	DECLARE @TransactionName varchar(20) = 'Transactional';
	declare @err nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
		update dbo.Operarios_histasigjefefiscal set vfechaFin=@fechaCambio,vactual_id=NULL where userJefe_id=@p_userJefe_id and vfechaFin is NULL
		delete from dbo.Operarios_asigjefefiscal where userJefe_id=@p_userJefe_id;
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH 
		set @err= ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@err);
	END CATCH

	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[asigjefefiscal_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[asigjefefiscal_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_userJefe_id int;
		DECLARE @p_userFiscal_id int ;
		DECLARE @p_id int;

		select @p_userJefe_id="value" from OpenJson(@json) where "key"='userJefe_id';
		select @p_userFiscal_id="value" from OpenJson(@json) where "key"='userFiscal_id';
		select @p_id="value" from OpenJson(@json) where "key"='id';
		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histasigjefefiscal where vactual_id=@p_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histasigjefefiscal(userJefe_id,userFiscal_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
				select userJefe_id,userFiscal_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id from dbo.Operarios_asigjefefiscal where id=@p_id;
			end
			update dbo.Operarios_histasigjefefiscal set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro;
			set @tmp1_vregistro=@tmp1_vregistro+1;
			INSERT INTO dbo.Operarios_histasigjefefiscal(userJefe_id,userFiscal_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
			select @p_userJefe_id,@p_userFiscal_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id
			update dbo.Operarios_asigjefefiscal set 
				 userJefe_id=@p_userJefe_id,userFiscal_id=@p_userFiscal_id where id=@p_id;
		end
		if  @p_id is NULL
		begin
			set @tmp1_vregistro=1;
			INSERT INTO dbo.Operarios_asigjefefiscal(userJefe_id,userFiscal_id)
			select @p_userJefe_id,@p_userFiscal_id;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histasigjefefiscal(userJefe_id,userFiscal_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
			select @p_userJefe_id,@p_userFiscal_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id
		end
		SET @retorno=0;
		Select @retorno as resultado;
END

GO
/****** Object:  StoredProcedure [dbo].[asignacion_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE       PROCEDURE [dbo].[asignacion_manager]   
	@json_cab nvarchar(max),
	@asig_cab int,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		DECLARE @hrm0_id int;
		DECLARE @hrm0_lunEnt time;
		DECLARE @hrm0_lunSal time;
		DECLARE @hrm0_marEnt time;
		DECLARE @hrm0_marSal time;
		DECLARE @hrm0_mieEnt time;
		DECLARE @hrm0_mieSal time;
		DECLARE @hrm0_jueEnt time;
		DECLARE @hrm0_jueSal time;
		DECLARE @hrm0_vieEnt time;
		DECLARE @hrm0_vieSal time;
		DECLARE @hrm0_sabEnt time;
		DECLARE @hrm0_sabSal time;
		DECLARE @hrm0_domEnt time;
		DECLARE @hrm0_domSal time;
		DECLARE @hrm0_asignacionCab_id int;
		DECLARE @hrm0_operario_id int;
		DECLARE @hrm0_fechaInicio date;
		DECLARE @hrm0_totalHoras nvarchar(max);
		DECLARE @hrm0_numTotalHoras int
		DECLARE @hrm0_fechaFin date;
		DECLARE @hrm0_supervisor bit;
		DECLARE @hrm0_perfil_id int;
		declare @tmp1_vregistro int;
		DECLARE @hrm0_eliminado nvarchar(max);
		SET @fechaCambio=CURRENT_TIMESTAMP;
			DECLARE @RC int;
			DECLARE @tmp int;
			
			EXECUTE @RC = [dbo].[asignacioncab_trg] @json_cab,@fechaCambio,@retorno

			INSERT INTO dbo.Operarios_asignaciondet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,eliminado,numTotalHoras)
			select perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,eliminado,numTotalHoras from dbo.Operarios_asignaciondettemp where asignacionCab_id=@asig_cab and eliminado='False'
				


			/*det no borrados*/
			DECLARE cursorIt CURSOR LOCAL FOR SELECT id,lunEnt,lunSal,marEnt,marSal,mieEnt,mieSal,jueEnt,jueSal,vieEnt,vieSal,sabEnt,sabSal,domEnt,domSal,asignacionCab_id,operario_id,fechaInicio,totalHoras,fechaFin,supervisor,perfil_id,eliminado,numTotalHoras FROM dbo.Operarios_asignaciondet where asignacionCab_id=@asig_cab
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @hrm0_id,@hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id,@hrm0_eliminado,@hrm0_numTotalHoras
			WHILE @@FETCH_STATUS = 0
			BEGIN
				select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histasignacioncab where vactual_id=@asig_cab
				if @tmp1_vregistro is NULL
				begin
					set @tmp1_vregistro=1;
					INSERT INTO dbo.Operarios_histasignaciondet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalHoras)
					select perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,@fechaCambio,NULL,@tmp1_vregistro,@hrm0_id,numTotalHoras from dbo.Operarios_asignaciondet where id=@hrm0_id;
				end
				update dbo.Operarios_histasignaciondet set vfechaFin=@fechaCambio where vactual_id=@hrm0_id and vregistro=@tmp1_vregistro-1;
				if @hrm0_eliminado is not NULL and @hrm0_eliminado=0
				begin
					INSERT INTO dbo.Operarios_histasignaciondet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalHoras)
					select @hrm0_perfil_id,@hrm0_supervisor,@hrm0_fechaFin,@hrm0_totalHoras,@hrm0_fechaInicio,@hrm0_operario_id,@hrm0_asignacionCab_id,@hrm0_domSal,@hrm0_domEnt,@hrm0_sabSal,@hrm0_sabEnt,@hrm0_vieSal,@hrm0_vieEnt,@hrm0_jueSal,@hrm0_jueEnt,@hrm0_mieSal,@hrm0_mieEnt,@hrm0_marSal,@hrm0_marEnt,@hrm0_lunSal,@hrm0_lunEnt,@fechaCambio,NULL,@tmp1_vregistro,@hrm0_id,@hrm0_numTotalHoras
				end
				if @hrm0_eliminado is not NULL and @hrm0_eliminado=1
				begin
        			update Operarios_histasignaciondet set vactual_id=NULL where vactual_id=@hrm0_id;
					delete from dbo.Operarios_asignaciondettemp  where  asignacionDet_original_id = @hrm0_id ;
					delete from dbo.Operarios_remplazosdet where  Asignacion_id = @hrm0_id;
					delete from dbo.Operarios_asignacionesprocesadas where  asignacionDet_id =@hrm0_id;
					delete from dbo.Operarios_alertaresp where  id_alerta_id in (select id from dbo.Operarios_alertas where Asignacion_id=@hrm0_id);
					delete from dbo.Operarios_cupoutilizado where horasProcesadas_id in (select id from dbo.Operarios_horasprocesadas where asignacionDet_id =@hrm0_id);
					delete from dbo.Operarios_horasprocesadas where asignacionDet_id=@hrm0_id;
					delete from dbo.Operarios_remplazoscab where  alertaId_id in (select id from dbo.Operarios_alertas where Asignacion_id=@hrm0_id);
					delete from dbo.Operarios_alertas where  Asignacion_id =@hrm0_id;
					delete from dbo.Operarios_asignaciondet  where id=@hrm0_id;
				end
			FETCH NEXT FROM cursorIt INTO @hrm0_id,@hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id,@hrm0_eliminado,@hrm0_numTotalHoras
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt
			delete from dbo.Operarios_asignaciondettemp where asignacionCab_id=@asig_cab
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		SET @retorno=1;
		ROLLBACK TRAN @TransactionName; 
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
		Select 1 as resultado;
		RETURN 1;
	END CATCH
	Select 0 as resultado;
	RETURN 0;

END	

GO
/****** Object:  StoredProcedure [dbo].[asignacioncab_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[asignacioncab_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_usuario_id int;
		DECLARE @p_puntoServicio_id int;
		DECLARE @p_totalasignado nvarchar(max);
		DECLARE @p_numTotalasignado int;
		DECLARE @p_fechaUltimaMod datetime2 ;
		DECLARE @p_id int;

		select @p_usuario_id="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
		select @p_puntoServicio_id="value" from OpenJson(@json) where "key"='puntoServicio_id' and "value"!='None';
		select @p_totalasignado="value" from OpenJson(@json) where "key"='totalasignado' and "value"!='None';
		select @p_numTotalasignado="value" from OpenJson(@json) where "key"='numTotalAsignado' and "value"!='None';
		select @p_fechaUltimaMod="value" from OpenJson(@json) where "key"='fechaUltimaMod' and  "value"!='None' and "value"!='00';

		if @p_fechaUltimaMod is NULL
		begin
			set @p_fechaUltimaMod = CURRENT_TIMESTAMP
		end

		select @p_id=cast("value" as int) from OpenJson(@json) where "key"='id' and "value"!='None';
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histasignacioncab where vactual_id=@p_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histasignacioncab(usuario_id,puntoServicio_id,totalasignado,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,reAsignar,numTotalAsignado)
				select usuario_id,puntoServicio_id,totalasignado,fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,'False',numTotalasignado from dbo.Operarios_asignacioncab where id=@p_id;
			end
			update dbo.Operarios_histasignacioncab set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro;
			set @tmp1_vregistro=@tmp1_vregistro+1;
			INSERT INTO dbo.Operarios_histasignacioncab(usuario_id,puntoServicio_id,totalasignado,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,reAsignar,numTotalAsignado)
			select @p_usuario_id,@p_puntoServicio_id,@p_totalasignado,@p_fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,'False',@p_numTotalasignado
			update dbo.Operarios_asignacioncab set 
				 usuario_id=@p_usuario_id,puntoServicio_id=@p_puntoServicio_id,totalasignado=@p_totalasignado,fechaUltimaMod=@p_fechaUltimaMod,numTotalAsignado=@p_numTotalasignado where id=@p_id;
		end
		if  @p_id is NULL
		begin
			set @tmp1_vregistro=1;
			INSERT INTO dbo.Operarios_asignacioncab(usuario_id,puntoServicio_id,totalasignado,fechaUltimaMod,numTotalAsignado)
			select @p_usuario_id,@p_puntoServicio_id,@p_totalasignado,@p_fechaUltimaMod,@p_numTotalasignado;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histasignacioncab(usuario_id,puntoServicio_id,totalasignado,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalAsignado)
			select @p_usuario_id,@p_puntoServicio_id,@p_totalasignado,@p_fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotalasignado
		end
		SET @retorno=0;
		return 0;
END
GO
/****** Object:  StoredProcedure [dbo].[asignaciondet_tmptrg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE     PROCEDURE [dbo].[asignaciondet_tmptrg]   
	@json nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		declare @fechaCambio datetime;
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_perfil_id int;
		DECLARE @p_supervisor bit;
		DECLARE @p_totalHoras nvarchar(max);		
		DECLARE @p_numTotalHoras int;
		DECLARE @p_operario_id int;
		DECLARE @p_asignacionCab_id int;
		DECLARE @p_reemplazoCab_id int;
		DECLARE @p_asignacionDet_id int;

		set @fechaCambio= CURRENT_TIMESTAMP;
		DECLARE @p_domSal time;
		DECLARE @p_domEnt time;
		DECLARE @p_sabSal time;
		DECLARE @p_sabEnt time;
		DECLARE @p_vieSal time;
		DECLARE @p_vieEnt time;
		DECLARE @p_jueSal time;
		DECLARE @p_jueEnt time;
		DECLARE @p_mieSal time;
		DECLARE @p_mieEnt time;
		DECLARE @p_marSal time;
		DECLARE @p_marEnt time;
		DECLARE @p_lunSal time;
		DECLARE @p_lunEnt time;
		DECLARE @p_id int;

		select @p_perfil_id="value" from OpenJson(@json) where "key"='perfil_id' and "value"!='None';
		select @p_supervisor="value" from OpenJson(@json) where "key"='supervisor' and "value"!='None';
		if @p_supervisor is NULL
		begin
			set @p_supervisor='False'
		end
		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @p_totalHoras="value" from OpenJson(@json) where "key"='totalHoras' and "value"!='None' and "value"!='00';
		select @p_numTotalHoras="value" from OpenJson(@json) where "key"='numTotalHoras' and "value"!='None' and "value"!='00';
		select @p_fechaInicio=convert(date,"value",103) from OpenJson(@json) where "key"='fechaInicio' and "value"!='None';
		select @p_fechaFin=convert(date,"value",103) from OpenJson(@json) where "key"='fechaFin' and "value"!='None';	
		select @p_operario_id="value" from OpenJson(@json) where "key"='operario_id' and "value"!='None' and "value"!='';
		select @p_asignacionCab_id="value" from OpenJson(@json) where "key"='asignacionCab_id' and "value"!='None' and "value"!='' ;
		select @p_reemplazoCab_id="value" from OpenJson(@json) where "key"='reemplazoCab_id' and "value"!='None' and "value"!='';
		select @p_asignacionDet_id="value" from OpenJson(@json) where "key"='asignacionDet_id' and "value"!='None' and "value"!='';
		select @p_domSal=cast("value" as time) from OpenJson(@json) where "key"='domSal' and "value"!='None';
		select @p_domEnt=cast("value" as time) from OpenJson(@json) where "key"='domEnt' and "value"!='None';
		select @p_sabSal=cast("value" as time) from OpenJson(@json) where "key"='sabSal' and "value"!='None';
		select @p_sabEnt=cast("value" as time) from OpenJson(@json) where "key"='sabEnt' and "value"!='None';
		select @p_vieSal=cast("value" as time) from OpenJson(@json) where "key"='vieSal' and "value"!='None';
		select @p_vieEnt=cast("value" as time) from OpenJson(@json) where "key"='vieEnt' and "value"!='None';
		select @p_jueSal=cast("value" as time) from OpenJson(@json) where "key"='jueSal' and "value"!='None';
		select @p_jueEnt=cast("value" as time) from OpenJson(@json) where "key"='jueEnt' and "value"!='None';
		select @p_mieSal=cast("value" as time) from OpenJson(@json) where "key"='mieSal' and "value"!='None';
		select @p_mieEnt=cast("value" as time) from OpenJson(@json) where "key"='mieEnt' and "value"!='None';
		select @p_marSal=cast("value" as time) from OpenJson(@json) where "key"='marSal' and "value"!='None';
		select @p_marEnt=cast("value" as time) from OpenJson(@json) where "key"='marEnt' and "value"!='None';
		select @p_lunSal=cast("value" as time) from OpenJson(@json) where "key"='lunSal' and "value"!='None';
		select @p_lunEnt=cast("value" as time) from OpenJson(@json) where "key"='lunEnt' and "value"!='None';
		select @p_id="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		
		INSERT INTO dbo.Operarios_asignaciondettemp(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,eliminado,fechaCreacion,remplazosCab_id,asignacionDet_original_id,numTotalHoras)
		select @p_perfil_id,@p_supervisor,@p_fechaFin,@p_totalHoras,@p_fechaInicio,@p_operario_id,@p_asignacionCab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,'False',CURRENT_TIMESTAMP,@p_reemplazoCab_id,@p_asignacionDet_id,@p_numTotalHoras;
			
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[asignaciondet_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[asignaciondet_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_perfil_id int;
		DECLARE @p_supervisor bit;
		DECLARE @p_totalHoras nvarchar(max);		
		DECLARE @p_operario_id int;
		DECLARE @p_asignacionCab_id int;
		DECLARE @p_numTotalHoras int;
		DECLARE @p_domSal time;
		DECLARE @p_domEnt time;
		DECLARE @p_sabSal time;
		DECLARE @p_sabEnt time;
		DECLARE @p_vieSal time;
		DECLARE @p_vieEnt time;
		DECLARE @p_jueSal time;
		DECLARE @p_jueEnt time;
		DECLARE @p_mieSal time;
		DECLARE @p_mieEnt time;
		DECLARE @p_marSal time;
		DECLARE @p_marEnt time;
		DECLARE @p_lunSal time;
		DECLARE @p_lunEnt time;
		DECLARE @p_id int;

		select @p_perfil_id="value" from OpenJson(@json) where "key"='perfil_id' and "value"!='None';
		select @p_supervisor="value" from OpenJson(@json) where "key"='supervisor';
		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @p_totalHoras="value" from OpenJson(@json) where "key"='totalHoras' and "value"!='None' and "value"!='00';
		select @p_numTotalHoras="value" from OpenJson(@json) where "key"='numTotalHoras' and "value"!='None' and "value"!='00';
		select @p_fechaInicio=cast("value" as date) from OpenJson(@json) where "key"='fechaInicio' and "value"!='None';
		select @p_fechaFin=cast("value" as date) from OpenJson(@json) where "key"='fechaFin' and "value"!='None';	
		select @p_operario_id="value" from OpenJson(@json) where "key"='operario_id' and "value"!='None';
		select @p_asignacionCab_id="value" from OpenJson(@json) where "key"='asignacionCab_id';
		select @p_domSal=cast("value" as time) from OpenJson(@json) where "key"='domSal' and "value"!='None';
		select @p_domEnt=cast("value" as time) from OpenJson(@json) where "key"='domEnt' and "value"!='None';
		select @p_sabSal=cast("value" as time) from OpenJson(@json) where "key"='sabSal' and "value"!='None';
		select @p_sabEnt=cast("value" as time) from OpenJson(@json) where "key"='sabEnt' and "value"!='None';
		select @p_vieSal=cast("value" as time) from OpenJson(@json) where "key"='vieSal' and "value"!='None';
		select @p_vieEnt=cast("value" as time) from OpenJson(@json) where "key"='vieEnt' and "value"!='None';
		select @p_jueSal=cast("value" as time) from OpenJson(@json) where "key"='jueSal' and "value"!='None';
		select @p_jueEnt=cast("value" as time) from OpenJson(@json) where "key"='jueEnt' and "value"!='None';
		select @p_mieSal=cast("value" as time) from OpenJson(@json) where "key"='mieSal' and "value"!='None';
		select @p_mieEnt=cast("value" as time) from OpenJson(@json) where "key"='mieEnt' and "value"!='None';
		select @p_marSal=cast("value" as time) from OpenJson(@json) where "key"='marSal' and "value"!='None';
		select @p_marEnt=cast("value" as time) from OpenJson(@json) where "key"='marEnt' and "value"!='None';
		select @p_lunSal=cast("value" as time) from OpenJson(@json) where "key"='lunSal' and "value"!='None';
		select @p_lunEnt=cast("value" as time) from OpenJson(@json) where "key"='lunEnt' and "value"!='None';
		select @p_id="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histasignacioncab where vactual_id=@p_asignacionCab_id
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histasignaciondet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalHoras)
				select perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotalHoras from dbo.Operarios_asignaciondet where id=@p_id;
			end
			update dbo.Operarios_histasignaciondet set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				INSERT INTO dbo.Operarios_histasignaciondet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalHoras)
				select @p_perfil_id,@p_supervisor,@p_fechaFin,@p_totalHoras,@p_fechaInicio,@p_operario_id,@p_asignacionCab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotalHoras
				update dbo.Operarios_asignaciondet set 
					 perfil_id=@p_perfil_id,supervisor=@p_supervisor,fechaFin=@p_fechaFin,totalHoras=@p_totalHoras,fechaInicio=@p_fechaInicio,operario_id=@p_operario_id,asignacionCab_id=@p_asignacionCab_id,domSal=@p_domSal,domEnt=@p_domEnt,sabSal=@p_sabSal,sabEnt=@p_sabEnt,vieSal=@p_vieSal,vieEnt=@p_vieEnt,jueSal=@p_jueSal,jueEnt=@p_jueEnt,mieSal=@p_mieSal,mieEnt=@p_mieEnt,marSal=@p_marSal,marEnt=@p_marEnt,lunSal=@p_lunSal,lunEnt=@p_lunEnt,numTotalHoras=@p_numTotalHoras where id=@p_id;
			end

			if @delete is not NULL and @delete='True'
			begin
                -- insert en hist updat hist set vactual_id=NULL where vactual_id=@p_id; delete where  where id=@p_id;
				--INSERT INTO dbo.Operarios_histasignaciondet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id)
				--select @p_perfil_id,@p_supervisor,@p_fechaFin,@p_totalHoras,@p_fechaInicio,@p_operario_id,@p_asignacionCab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@fechaCambio,@,@tmp1_vregistro,@p_id
			    update Operarios_histasignaciondet set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_asignaciondet  where id=@p_id;
			end

			

		end
		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histasignacioncab where vactual_id=@p_asignacionCab_id;
			INSERT INTO dbo.Operarios_asignaciondet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,numTotalHoras)
			select @p_perfil_id,@p_supervisor,@p_fechaFin,@p_totalHoras,@p_fechaInicio,@p_operario_id,@p_asignacionCab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@p_numTotalHoras;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histasignaciondet(perfil_id,supervisor,fechaFin,totalHoras,fechaInicio,operario_id,asignacionCab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotalHoras)
			select @p_perfil_id,@p_supervisor,@p_fechaFin,@p_totalHoras,@p_fechaInicio,@p_operario_id,@p_asignacionCab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotalHoras
		end
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[asigpsfisc_des_trigger]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE        PROCEDURE [dbo].[asigpsfisc_des_trigger]   
  

	@p_userFiscal_id int,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;
	DECLARE @TransactionName varchar(20) = 'Transactional';
	declare @err nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
		update dbo.Operarios_histasigfiscalpuntoservicio set vfechaFin=@fechaCambio,vactual_id=NULL where userFiscal_id=@p_userFiscal_id and vfechaFin is NULL
		delete from dbo.Operarios_asigfiscalpuntoservicio where userFiscal_id=@p_userFiscal_id;
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH 
		set @err= ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@err);
	END CATCH

	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[clean_asignaciondet]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE          PROCEDURE [dbo].[clean_asignaciondet]
	@p_asignacionCab_id int,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		declare @fechaCambio datetime;
		set @fechaCambio= CURRENT_TIMESTAMP;
		update dbo.Operarios_asignaciondet set eliminado='False' where asignacionCab_id=@p_asignacionCab_id;
		delete from dbo.Operarios_asignaciondettemp where asignacionCab_id=@p_asignacionCab_id;
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[generadorLimpieza]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE         PROCEDURE [dbo].[generadorLimpieza]   
	@p_revcabID int,
	@retorno int OUTPUT
	--@operario int
AS   
	BEGIN
	SET NOCOUNT ON;
		DECLARE @TransactionName varchar(20) = 'Transactional';
		Declare @err_msg nvarchar(max);
		BEGIN TRAN @TransactionName 
		BEGIN TRY
			Declare @fechaCambio datetime;
			set @fechaCambio=CURRENT_TIMESTAMP;
			Declare @plancab int;
			Declare @puntoservice int;
			declare @tipoServ int;
			Declare @veractual int;
			Declare @userchange int;
			Declare @frecuencia nvarchar(3);
		    Declare @cantHoras nvarchar(8);
			Declare @revCantHoras nvarchar(8);
			Declare @revNumCantHoras int;
			Declare @area nvarchar(50);
			Declare @cantidad int;
			Declare @sector nvarchar(50);
			Declare @tipoHora int;
		    Declare @especialista int;
		    declare @numCantHoras int;
			declare @p_partir int;
			declare @fi datetime;
			declare @ff datetime;
			
			select top(1) @plancab=placab.id,@puntoservice=revcab.puntoServicio_id,@userchange=revcab.usuario_id,@fi=revcab.fechaInicio,@ff=revcab.fechaFin,
			@revCantHoras=revcab.cantidadHrEsp,@revNumCantHoras= revcab.numCantidadHrEsp
			from dbo.Operarios_relevamientocab revcab
			left join dbo.Operarios_puntoservicio ps on ps.id=revcab.puntoServicio_id
			left join dbo.Operarios_planificacioncab placab on placab.puntoServicio_id=ps.id
			where revcab.id=@p_revcabID

			if @plancab is NULL
			begin
				insert into dbo.Operarios_planificacioncab(fecha,rePlanificar,puntoServicio_id) 
				values(CURRENT_TIMESTAMP,'False',@puntoservice);
				set @plancab=SCOPE_IDENTITY();

			end

			select @veractual=max(vregistro) from dbo.Operarios_histplanificacioncab where vactual_id=@plancab;
			if @veractual is NULL
			begin
				set @veractual=1;
			end
			/*Debo actualizar el total de horas?*/
			if @ff is null
			begin
				set @ff=dateadd(YEAR,1,@fi)
			end
			update dbo.Operarios_planificacioncab set usuario_id=@userchange,cantHorasEsp=@revCantHoras,numCantHorasEsp=@numCantHoras where id=@plancab;
			update [dbo].[Operarios_histplanificacioncab] set vfechaFin=@fechaCambio,vactual_id=NULL where vactual_id=@plancab;
			INSERT INTO [dbo].[Operarios_histplanificacioncab]
           ([fecha]
           ,[cantidad]
           ,[cantHoras]
           ,[cantHorasNoc]
           ,[cantHorasEsp]
           ,[rePlanificar]
           ,[vfechaInicio]
           ,[vfechaFin]
           ,[vregistro]
           ,[puntoServicio_id]
           ,[vactual_id]
           ,[usuario_id]
           ,[numCantHoras]
           ,[numCantHorasEsp]
           ,[numCantHorasNoc])
			select
           [fecha]
           ,[cantidad]
           ,[cantHoras]
           ,[cantHorasNoc]
           ,[cantHorasEsp]
           ,[rePlanificar]
           ,@fechaCambio
           ,NULL
           ,@veractual+1
           ,[puntoServicio_id]
           ,@plancab
           ,@userchange
           ,[numCantHoras]
           ,[numCantHorasEsp]
           ,[numCantHorasNoc] from  [Operarios_histplanificacioncab] where id=@plancab
			
			update dbo.Operarios_histplanificacionope set vfechaFin=@fechaCambio,vactual_id=NULL where planificacionCab_id=@plancab and vfechaFin is NULL;
			INSERT INTO [dbo].[Operarios_histplanificacionope]
           ([cantidad]
           ,[lun]
           ,[mar]
           ,[mie]
           ,[jue]
           ,[vie]
           ,[sab]
           ,[dom]
           ,[fer]
           ,[ent]
           ,[sal]
           ,[corte]
           ,[total]
           ,[vfechaInicio]
           ,[vfechaFin]
           ,[vregistro]
           ,[especialista_id]
           ,[planificacionCab_id]
           ,[vactual_id]
           ,[numTotal])
		   select 
           [cantidad]
           ,[lun]
           ,[mar]
           ,[mie]
           ,[jue]
           ,[vie]
           ,[sab]
           ,[dom]
           ,[fer]
           ,[ent]
           ,[sal]
           ,[corte]
           ,[total]
           ,@fechaCambio
           ,NULL
           ,@veractual+1
           ,[especialista_id]
           ,[planificacionCab_id]
           ,id
           ,[numTotal] from [dbo].[Operarios_planificacionope] where planificacionCab_id=@plancab
		   
		   
		   update [dbo].[Operarios_histplanificacionesp] set vfechaFin=@fechaCambio,vactual_id=NULL where planificacionCab_id=@plancab and vfechaFin is NULL;		   
		   /*borro las planificaciones futuras y que no tienen activdad*/
		   select 1;
		   delete plaesp from dbo.Operarios_planificacionesp plaesp
			left join dbo.Operarios_planificacioncab placab on  plaesp.planificacionCab_id=placab.id
			left join dbo.Operarios_puntoservicio ps on ps.id=placab.puntoServicio_id
			left join dbo.Operarios_relevamientocab revcab on revcab.puntoServicio_id=ps.id
			left join dbo.Operarios_actividadcab actcab on actcab.planificacionEsp_id=plaesp.id
			where revcab.id=@p_revcabID and plaesp.fechaLimpProf>=@fechaCambio and actcab.id is NULL 

			
		   DECLARE cursorIt CURSOR LOCAL FOR SELECT frecuencia,cantHoras,perfil_id,numCantHoras,area,cantidad,sector,tipoHora_id,tipo_id FROM dbo.Operarios_relevamientoesp where relevamientoCab_id=@p_revcabID;
		   OPEN cursorIt
		   FETCH NEXT FROM cursorIt INTO @frecuencia,@cantHoras,@especialista,@numCantHoras,@area,@cantidad,@sector,@tipoHora,@tipoServ
		   WHILE @@FETCH_STATUS = 0
		   BEGIN
				select @p_partir = case when @frecuencia ='MEN' then 1 
									  when @frecuencia ='BIM' then 2
									  when @frecuencia ='TRI' then 3
									  when @frecuencia ='CUA' then 4
									  when @frecuencia ='SEL' then 6
									  when @frecuencia ='ANU' then 12 else 1 end;
				drop table  if exists #meses;
				CREATE table #meses (
					inicio datetime,
					fin datetime,
					dias int,
					mes int,
					anho int
				);
				insert into #meses EXEC[dbo].[partirMesesXN]
					@fechaInicio = @fi,
					@fechaFin = @ff,
					@partir=@p_partir;

				delete from #meses where inicio in(
					select fechaLimpProf from dbo.Operarios_planificacionesp where 
					planificacionCab_id=@plancab and 
					frecuencia=@frecuencia and 
					cantHoras=@cantHoras and 
					especialista_id=@especialista and
					@numCantHoras=numCantHoras and
					@area=@area and
					cantidad=@cantidad
					and sector=@sector
					and tipoHora_id=@tipoHora
					and tipo_id=@tipoServ);
				/*Ver el tipo de hora del elemento*/
				INSERT INTO [dbo].[Operarios_planificacionesp]
					([frecuencia]
				   ,[cantHoras]
				   ,[fechaLimpProf]
				   ,[especialista_id]
				   ,[planificacionCab_id]
				   ,[tipo_id]
				   ,[numCantHoras]
				   ,[estado],area,cantidad,sector,tipoHora_id)
				   select @frecuencia,@cantHoras,cast(mes.fin as date),@especialista,@plancab,@tipoServ,@numCantHoras,'PVC',@area,@cantidad,@sector,@tipoHora
				   from #meses mes where mes.inicio>=GETDATE()
				FETCH NEXT FROM cursorIt INTO  @frecuencia,@cantHoras,@especialista,@numCantHoras,@area,@cantidad,@sector,@tipoHora,@tipoServ	
		   END
		   CLOSE cursorIt
		   DEALLOCATE cursorIt
		   
		   INSERT INTO [dbo].[Operarios_histplanificacionesp]
           ([frecuencia]
           ,[cantHoras]
           ,[fechaLimpProf]
           ,[vfechaInicio]
           ,[vfechaFin]
           ,[vregistro]
           ,[especialista_id]
           ,[planificacionCab_id]
           ,[tipo_id]
           ,[vactual_id]
           ,[numCantHoras]
           ,[estado],area,sector,cantidad,tipoHora_id)
			select plaesp.frecuencia
           ,plaesp.cantHoras
           ,plaesp.fechaLimpProf
           ,@fechaCambio
           ,NULL
           ,@veractual+1
           ,plaesp.especialista_id
           ,plaesp.planificacionCab_id
           ,plaesp.tipo_id
           ,plaesp.id
           ,plaesp.numCantHoras
           ,plaesp.estado,plaesp.area,plaesp.sector,plaesp.cantidad,plaesp.tipoHora_id from dbo.Operarios_planificacionesp plaesp
			where planificacionCab_id=@plancab;
			COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,'Cabecera: '+@p_revcabID);
	END CATCH
	Select @retorno as resultado;
END

GO
/****** Object:  StoredProcedure [dbo].[generadorSincronizacion]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

create      PROCEDURE [dbo].[generadorSincronizacion]   
	@mes int,
	@anho int,
	@usuario int,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;

		create table #sincro_temp(
		NumCedulaOperario nvarchar(30),
		totalHora int,
		totalMinuto int,
		mes int,
		anho int,
		tipoHora nvarchar(30),
		puntoServicio_id int
		);

		insert into #sincro_temp(NumCedulaOperario,totalHora,totalMinuto,mes,anho,tipoHora,puntoServicio_id)
		SELECT
      [NumCedulaOperario],
      sum(datepart(HH,total))*60 as totalHora,
	  sum(datepart(MINUTE,total))as totalMinuto
      ,datepart(MM,fecha) as mes
	  ,datepart(YYYY,fecha) as anho
      ,[TipoHora]
      ,[puntoServicio_id]
	 FROM [dbo].[Operarios_horasprocesadas] group by NumCedulaOperario,TipoHora,puntoServicio_id,datepart(YYYY,fecha),datepart(MM,fecha) having datepart(YYYY,fecha)=@anho and datepart(MM,fecha)=@mes ;
		Declare @proceso int;	
		INSERT INTO [dbo].[Operarios_procesosincronizacion]
           ([mes]
           ,[anho]
           ,[Fecha]
           ,[inicioSinc]
           ,[finSinc]
           ,[usuario_id])
		values(@mes,@anho,cast(GETDATE() as date),CURRENT_TIMESTAMP,NULL,@usuario);
		select @proceso=SCOPE_IDENTITY();
		Declare @operario nvarchar(30);
		Declare @operario_id int;
		Declare @nombreCompleto nvarchar(140);
		Declare @sincCab int;
		DECLARE cursorIt CURSOR LOCAL FOR SELECT distinct NumCedulaOperario from #sincro_temp where mes=@mes and anho=@anho
		OPEN cursorIt
		FETCH NEXT FROM cursorIt INTO @operario
		WHILE @@FETCH_STATUS = 0
		BEGIN
			select @operario_id=id,@nombreCompleto=concat(nombre,apellido) from dbo.Operarios_operario where numCedula=@operario;
			if @operario_id is not NULL
			begin
				INSERT INTO [dbo].[Operarios_sincronizacioncab]
			   ([nombrePersona]
			   ,[mes]
			   ,[anho]
			   ,[Fecha]
			   ,[cantidad]
			   ,[enviado]
			   ,[operario_id],
			   proceso_id) values(@nombreCompleto,@mes,@anho,CURRENT_TIMESTAMP,0,'False',@operario_id,@proceso);
				select @sincCab=SCOPE_IDENTITY();
				INSERT INTO [dbo].[Operarios_sincronizaciondet]
			   ([CodPersona]
			   ,[tipoHora]
			   ,[CodUbicacion]
			   ,[cantidad]
			   ,[operario_id]
			   ,[puntoServicio_id]
			   ,[sincronizacionCab_id]) 
			   select @operario,tipoHora,ps.CodPuntoServicio,totalHora+totalMinuto,@operario_id,puntoServicio_id,@sincCab 
				from #sincro_temp inner join dbo.Operarios_puntoservicio ps on ps.id = puntoServicio_id
				where mes=@mes and anho=@anho and NumCedulaOperario=@operario
			end

		FETCH NEXT FROM cursorIt INTO @operario
		END
		CLOSE cursorIt
		DEALLOCATE cursorIt
		update dbo.Operarios_procesosincronizacion set finSinc=CURRENT_TIMESTAMP where id=@proceso;
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		SET @retorno=1;
		ROLLBACK TRAN @TransactionName; 
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		Select 1 as resultado;
		RETURN 1;
	END CATCH
	Select 0 as resultado;
	RETURN 0;

END	

GO
/****** Object:  StoredProcedure [dbo].[listar_asignaciones]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE         PROCEDURE [dbo].[listar_asignaciones]   
    @operario int,   
    @fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@tipo nvarchar(10),
	@reem_cab int
AS   
    BEGIN
		set nocount on;
		DECLARE @fechaFin date
		if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaFinOperario,103)	 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END
		INSERT INTO [dbo].[Operarios_asignaciondettemp]
           ([lunEnt]
           ,[lunSal]
           ,[marEnt]
           ,[marSal]
           ,[mieEnt]
           ,[mieSal]
           ,[jueEnt]
           ,[jueSal]
           ,[vieEnt]
           ,[vieSal]
           ,[sabEnt]
           ,[sabSal]
           ,[domEnt]
           ,[domSal]
           ,[fechaInicio]
           ,[fechaFin]
           ,[totalHoras]
           ,[supervisor]
           ,[eliminado]
           ,[fechaCreacion]
           ,[asignacionCab_id]
           ,[operario_id]
           ,[perfil_id]
           ,[asignacionDet_original_id]
           ,[remplazosCab_id],
		   numTotalHoras)
     SELECT [lunEnt]
			  ,[lunSal]
			  ,[marEnt]
			  ,[marSal]
			  ,[mieEnt]
			  ,[mieSal]
			  ,[jueEnt]
			  ,[jueSal]
			  ,[vieEnt]
			  ,[vieSal]
			  ,[sabEnt]
			  ,[sabSal]
			  ,[domEnt]
			  ,[domSal]
			  ,convert(date,@fechaInicioOperario,103)
			  ,case when  fechaFin is NULL OR fechaFin>@fechaFin then @fechaFin else fechaFin end
			  ,[totalHoras]
			  ,[supervisor]
			  ,[eliminado],CURRENT_TIMESTAMP
			   ,NULL
			   ,NULL
			   ,[perfil_id]
			   ,id
           ,@reem_cab,numTotalHoras FROM [dbo].[Operarios_asignaciondet] where operario_id=@operario 
		and fechaInicio<=convert(date,@fechaInicioOperario,103) and (fechaFin is NULL or fechaFin>=convert(date,@fechaInicioOperario,103))
		and id not in(select asignacionDet_original_id from dbo.Operarios_asignaciondettemp where remplazosCab_id=@reem_cab and (eliminado is NULL or eliminado='False'))


		SELECT * FROM dbo.Operarios_asignaciondettemp where remplazosCab_id=@reem_cab and (eliminado is NULL or eliminado='False')

	END
GO
/****** Object:  StoredProcedure [dbo].[listar_asignaciones2]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE           PROCEDURE [dbo].[listar_asignaciones2]   
    @operario int,   
    @fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@tipo nvarchar(10),
	@reem_cab int
AS   
    BEGIN
		set nocount on;
		DECLARE @fechaFin date
		if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaFinOperario,103)	 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END
		CREATE table #semanas (
			inicio datetime,
			fin datetime,
			dias int,
			semana int
		);
		declare @fi datetime;
		select @fi= convert(date,@fechaInicioOperario,103);
		insert into #semanas EXEC[dbo].[partirSemanas]
		@fechaInicio = @fi,
		@fechaFin = @fechaFin;

		
		INSERT INTO [dbo].[Operarios_asignaciondettemp]
           ([lunEnt]
           ,[lunSal]
           ,[marEnt]
           ,[marSal]
           ,[mieEnt]
           ,[mieSal]
           ,[jueEnt]
           ,[jueSal]
           ,[vieEnt]
           ,[vieSal]
           ,[sabEnt]
           ,[sabSal]
           ,[domEnt]
           ,[domSal]
           ,[fechaInicio]
           ,[fechaFin]
           ,[totalHoras]
           ,[supervisor]
           ,[eliminado]
           ,[fechaCreacion]
           ,[asignacionCab_id]
           ,[operario_id]
           ,[perfil_id]
           ,[asignacionDet_original_id]
           ,[remplazosCab_id],numTotalHoras)
     SELECT [lunEnt]
			  ,[lunSal]
			  ,[marEnt]
			  ,[marSal]
			  ,[mieEnt]
			  ,[mieSal]
			  ,[jueEnt]
			  ,[jueSal]
			  ,[vieEnt]
			  ,[vieSal]
			  ,[sabEnt]
			  ,[sabSal]
			  ,[domEnt]
			  ,[domSal]
			  ,ss.inicio,
			  case when fechaFin is Null then ss.fin when ss.fin>=fechaFin then fechaFin else ss.fin end
			  ,[totalHoras]
			  ,[supervisor]
			  ,[eliminado],CURRENT_TIMESTAMP
			   ,NULL
			   ,NULL
			   ,[perfil_id]
			   ,id
           ,@reem_cab,numTotalHoras FROM [dbo].[Operarios_asignaciondet] right join #semanas ss on ss.inicio<=fechaFin or fechaFin is NULL where  operario_id=@operario 
		and fechaInicio<=convert(date,@fechaInicioOperario,103) and (fechaFin is NULL or fechaFin>=convert(date,@fechaInicioOperario,103))
		and id not in(select asignacionDet_original_id from dbo.Operarios_asignaciondettemp where remplazosCab_id=@reem_cab and (eliminado is NULL or eliminado='False'))
		SELECT * FROM dbo.Operarios_asignaciondettemp where remplazosCab_id=@reem_cab and (eliminado is NULL or eliminado='False')

	END
GO
/****** Object:  StoredProcedure [dbo].[listar_asignaciones3]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[listar_asignaciones3]   
    @operario int,   
    @fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@tipo nvarchar(10),
	@reem_cab int
AS   
    BEGIN
		set nocount on;
		DECLARE @fechaFin date
		if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaFinOperario,103)	 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END
		CREATE  table #dias (
			fecha datetime,
			dia int		);
		declare @fi datetime;
		select @fi= convert(date,@fechaInicioOperario,103);
		insert into #dias EXEC[dbo].[partirDias]
		@fechaInicio = @fi,
		@fechaFin = @fechaFin;
		INSERT INTO [dbo].[Operarios_asignaciondettemp]
           ([lunEnt]
           ,[lunSal]
           ,[marEnt]
           ,[marSal]
           ,[mieEnt]
           ,[mieSal]
           ,[jueEnt]
           ,[jueSal]
           ,[vieEnt]
           ,[vieSal]
           ,[sabEnt]
           ,[sabSal]
           ,[domEnt]
           ,[domSal]
           ,[fechaInicio]
           ,[fechaFin]
           ,[totalHoras]
           ,[supervisor]
           ,[eliminado]
           ,[fechaCreacion]
           ,[asignacionCab_id]
           ,[operario_id]
           ,[perfil_id]
           ,[asignacionDet_original_id]
           ,[remplazosCab_id],numTotalHoras)
     SELECT		case when dd.dia = 1 then [lunEnt] else NULL end
			  ,case when dd.dia = 1 then [lunSal] else NULL end
			  ,case when dd.dia = 2 then [marEnt] else NULL end
			  ,case when dd.dia = 2 then [marSal] else NULL end
			  ,case when dd.dia = 3 then [mieEnt] else NULL end
			  ,case when dd.dia = 3 then [mieSal] else NULL end
			  ,case when dd.dia = 4 then [jueEnt] else NULL end
			  ,case when dd.dia = 4 then [jueSal] else NULL end
			  ,case when dd.dia = 5 then [vieEnt] else NULL end
			  ,case when dd.dia = 5 then [vieSal] else NULL end
			  ,case when dd.dia = 6 then [sabEnt] else NULL end
			  ,case when dd.dia = 6 then [sabSal] else NULL end
			  ,case when dd.dia = 7 then [domEnt] else NULL end
			  ,case when dd.dia = 7 then [domSal] else NULL end
			  ,dd.fecha,
			  dd.fecha
			  ,[totalHoras]
			  ,[supervisor]
			  ,[eliminado],CURRENT_TIMESTAMP
			   ,NULL
			   ,NULL
			   ,[perfil_id]
			   ,id
           ,@reem_cab,numTotalHoras FROM [dbo].[Operarios_asignaciondet] right join #dias dd on (dd.fecha<=fechaFin or fechaFin is NULL) and((dd.dia = 1 and lunEnt is not NULL)
			or (dd.dia = 1 and lunSal is not NULL)
			or (dd.dia = 2 and marEnt is not NULL)
			or (dd.dia = 2 and marSal is not NULL)
			or (dd.dia = 3 and mieEnt is not NULL)
			or (dd.dia = 3 and mieSal is not NULL)
			or (dd.dia = 4 and jueEnt is not NULL)
			or (dd.dia = 4 and jueSal is not NULL)
			or (dd.dia = 5 and vieEnt is not NULL)
			or (dd.dia = 5 and vieSal is not NULL)
			or (dd.dia = 6 and sabEnt is not NULL)
			or (dd.dia = 6 and sabSal is not NULL)
			or (dd.dia = 7 and domEnt is not NULL)
			or (dd.dia = 7 and domSal is not NULL))
			where  operario_id=@operario 
		and fechaInicio<=convert(date,@fechaInicioOperario,103) and (fechaFin is NULL or fechaFin>=convert(date,@fechaInicioOperario,103))
		and id not in(select asignacionDet_original_id from dbo.Operarios_asignaciondettemp where remplazosCab_id=@reem_cab and (eliminado is NULL or eliminado='False'))
		SELECT * FROM dbo.Operarios_asignaciondettemp where remplazosCab_id=@reem_cab and (eliminado is NULL or eliminado='False')

	END
GO
/****** Object:  StoredProcedure [dbo].[listar_asignaciones4]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE         PROCEDURE [dbo].[listar_asignaciones4]   
    @p_operario int,   
    @p_fechaInicioOperario nvarchar(10),
	@p_fechaFinOperario nvarchar(10),
	@p_tipo nvarchar(10),
	@p_reem_cab int
AS   
    BEGIN
		set nocount on;
		if lower(@p_tipo)='puntoserv'
		begin
			EXEC [dbo].[listar_asignaciones] @operario=@p_operario,@fechaInicioOperario=@p_fechaInicioOperario ,@fechaFinOperario=@p_fechaFinOperario,@tipo=@p_tipo,@reem_cab=@p_reem_cab            
		end
		else
		begin
			if lower(@p_tipo)='puntosem'
			begin
				EXEC [dbo].[listar_asignaciones2] @operario=@p_operario,@fechaInicioOperario=@p_fechaInicioOperario ,@fechaFinOperario=@p_fechaFinOperario,@tipo=@p_tipo,@reem_cab=@p_reem_cab            
			end
			else
			begin
				if lower(@p_tipo)='granular'
				begin
					EXEC [dbo].[listar_asignaciones3] @operario=@p_operario,@fechaInicioOperario=@p_fechaInicioOperario ,@fechaFinOperario=@p_fechaFinOperario,@tipo=@p_tipo,@reem_cab=@p_reem_cab            
				end
				else
				begin
					select null;
				end
			end
		end


	END
GO
/****** Object:  StoredProcedure [dbo].[listarLimpiezas]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE    PROCEDURE [dbo].[listarLimpiezas]   
	@p_placab int,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
			Declare @fechaCambio datetime;
			set @fechaCambio=CURRENT_TIMESTAMP;
			Declare @plancab int;
			Declare @veractual int;
			Declare @userchange int;
			Declare @frecuencia nvarchar(max);
		    Declare @cantHoras nvarchar(max);
		    Declare @especialista int;
		    declare @numCantHoras int;
			declare @p_partir int;
			declare @fi datetime;
			declare @ff datetime;
			
			select top(1) @fi=revcab.fechaInicio,@ff=revcab.fechaFin
			from dbo.Operarios_planificacioncab placab
			inner join dbo.Operarios_puntoservicio ps on ps.id=placab.puntoServicio_id
			inner join dbo.Operarios_relevamientocab revcab on revcab.puntoServicio_id=ps.id
			where placab.id=@p_placab;
			 /* ('PVC', 'POR VENCER'),
				('COV', 'CANCELADO O VENCIDO'),
				('VED', 'VENCE EN EL DIA'),
				('PGR', 'EN PROGRESO'),
				('FIN', 'FINALIZADA')*/
			update dbo.Operarios_planificacionesp set estado='COV' where 
				fechaLimpProf<Convert(date,CURRENT_TIMESTAMP) and 
				planificacionCab_id=@p_placab and estado!='FIN' and estado!='COV';
			update dbo.Operarios_planificacionesp set estado='VED' where 
				fechaLimpProf=Convert(date,CURRENT_TIMESTAMP) and 
				planificacionCab_id=@p_placab and estado!='FIN' and estado!='COV';
			if @ff is null
			begin
				set @ff=dateadd(YEAR,1,@fi)
			end
			CREATE table #meses (
					inicio datetime,
					fin datetime,
					dias int,
					mes int,
					anho int
				);
			insert into #meses EXEC[dbo].[partirMesesXN]
					@fechaInicio = @fi,
					@fechaFin = @ff,
					@partir=1;
			
			select case 
				when mes.mes =1 then 'Enero' 
				when mes.mes =2 then 'Febrero' 
				when mes.mes =3 then 'Marzo' 
				when mes.mes =4 then 'Abril' 
				when mes.mes =5 then 'Mayo' 
				when mes.mes =6 then 'Junio' 
				when mes.mes =7 then 'Julio' 
				when mes.mes =8 then 'Agosto' 
				when mes.mes =9 then 'Septiembre' 
				when mes.mes =10 then 'Octubre' 
				when mes.mes =11 then 'Noviembre' 
				else 'Diciembre' end  as 'mesNombre',
				mes.anho as 'anho',
				(select plaesp.*,case when act.numTotalAsignado is not NULL and plaesp.numCantHoras is not NULL and plaesp.numCantHoras>0 then Round((cast(act.numTotalAsignado as float)/cast(plaesp.numCantHoras as float))*100,2) else 0.0 end as 'actHoras',tipoHorario as 'tipoHorarioNombre',tips.tipoServicio as 'tipoServicioNombre',perfil.especializacion as 'especializacionNombre' from dbo.Operarios_planificacionesp plaesp left join dbo.Operarios_tipohorario tiph on plaesp.tipoHora_id=tiph.id left join dbo.Operarios_tiposervicio tips on tips.id=plaesp.tipo_id left join dbo.Operarios_actividadcab act on act.planificacionEsp_id=plaesp.id left join dbo.Operarios_especializacion perfil on perfil.id=plaesp.especialista_id  where plaesp.planificacionCab_id=@p_placab and  plaesp.frecuencia='MEN' and mes.mes=datepart(MM,plaesp.fechaLimpProf)  and mes.anho=datepart(YYYY,plaesp.fechaLimpProf) FOR JSON PATH) as 'mensual',
				(select plaesp.*,case when act.numTotalAsignado is not NULL and plaesp.numCantHoras is not NULL and plaesp.numCantHoras>0 then Round((cast(act.numTotalAsignado as float)/cast(plaesp.numCantHoras as float))*100,2) else 0.0 end as 'actHoras',tipoHorario as 'tipoHorarioNombre',tips.tipoServicio as 'tipoServicioNombre',perfil.especializacion as 'especializacionNombre' from dbo.Operarios_planificacionesp plaesp left join dbo.Operarios_tipohorario tiph on plaesp.tipoHora_id=tiph.id left join dbo.Operarios_tiposervicio tips on tips.id=plaesp.tipo_id left join dbo.Operarios_actividadcab act on act.planificacionEsp_id=plaesp.id left join dbo.Operarios_especializacion perfil on perfil.id=plaesp.especialista_id  where plaesp.planificacionCab_id=@p_placab and  plaesp.frecuencia='BIM' and mes.mes=datepart(MM,plaesp.fechaLimpProf)  and mes.anho=datepart(YYYY,plaesp.fechaLimpProf) FOR JSON PATH) as 'bimestral',
				(select plaesp.*,case when act.numTotalAsignado is not NULL and plaesp.numCantHoras is not NULL and plaesp.numCantHoras>0 then Round((cast(act.numTotalAsignado as float)/cast(plaesp.numCantHoras as float))*100,2) else 0.0 end as 'actHoras',tipoHorario as 'tipoHorarioNombre',tips.tipoServicio as 'tipoServicioNombre',perfil.especializacion as 'especializacionNombre' from dbo.Operarios_planificacionesp plaesp left join dbo.Operarios_tipohorario tiph on plaesp.tipoHora_id=tiph.id left join dbo.Operarios_tiposervicio tips on tips.id=plaesp.tipo_id left join dbo.Operarios_actividadcab act on act.planificacionEsp_id=plaesp.id left join dbo.Operarios_especializacion perfil on perfil.id=plaesp.especialista_id  where plaesp.planificacionCab_id=@p_placab and  plaesp.frecuencia='TRI' and mes.mes=datepart(MM,plaesp.fechaLimpProf)  and mes.anho=datepart(YYYY,plaesp.fechaLimpProf) FOR JSON PATH) as 'trimestral',
				(select plaesp.*,case when act.numTotalAsignado is not NULL and plaesp.numCantHoras is not NULL and plaesp.numCantHoras>0 then Round((cast(act.numTotalAsignado as float)/cast(plaesp.numCantHoras as float))*100,2) else 0.0 end as 'actHoras',tipoHorario as 'tipoHorarioNombre',tips.tipoServicio as 'tipoServicioNombre',perfil.especializacion as 'especializacionNombre' from dbo.Operarios_planificacionesp plaesp left join dbo.Operarios_tipohorario tiph on plaesp.tipoHora_id=tiph.id left join dbo.Operarios_tiposervicio tips on tips.id=plaesp.tipo_id left join dbo.Operarios_actividadcab act on act.planificacionEsp_id=plaesp.id left join dbo.Operarios_especializacion perfil on perfil.id=plaesp.especialista_id  where plaesp.planificacionCab_id=@p_placab and  plaesp.frecuencia='CUA' and mes.mes=datepart(MM,plaesp.fechaLimpProf)  and mes.anho=datepart(YYYY,plaesp.fechaLimpProf) FOR JSON PATH) as 'cuatrimestral',
				(select plaesp.*,case when act.numTotalAsignado is not NULL and plaesp.numCantHoras is not NULL and plaesp.numCantHoras>0 then Round((cast(act.numTotalAsignado as float)/cast(plaesp.numCantHoras as float))*100,2) else 0.0 end as 'actHoras',tipoHorario as 'tipoHorarioNombre',tips.tipoServicio as 'tipoServicioNombre',perfil.especializacion as 'especializacionNombre' from dbo.Operarios_planificacionesp plaesp left join dbo.Operarios_tipohorario tiph on plaesp.tipoHora_id=tiph.id left join dbo.Operarios_tiposervicio tips on tips.id=plaesp.tipo_id left join dbo.Operarios_actividadcab act on act.planificacionEsp_id=plaesp.id left join dbo.Operarios_especializacion perfil on perfil.id=plaesp.especialista_id  where plaesp.planificacionCab_id=@p_placab and  plaesp.frecuencia='SEL' and mes.mes=datepart(MM,plaesp.fechaLimpProf)  and mes.anho=datepart(YYYY,plaesp.fechaLimpProf) FOR JSON PATH) as 'semestral',
				(select plaesp.*,case when act.numTotalAsignado is not NULL and plaesp.numCantHoras is not NULL and plaesp.numCantHoras>0 then Round((cast(act.numTotalAsignado as float)/cast(plaesp.numCantHoras as float))*100,2) else 0.0 end as 'actHoras',tipoHorario as 'tipoHorarioNombre',tips.tipoServicio as 'tipoServicioNombre',perfil.especializacion as 'especializacionNombre' from dbo.Operarios_planificacionesp plaesp left join dbo.Operarios_tipohorario tiph on plaesp.tipoHora_id=tiph.id left join dbo.Operarios_tiposervicio tips on tips.id=plaesp.tipo_id left join dbo.Operarios_actividadcab act on act.planificacionEsp_id=plaesp.id left join dbo.Operarios_especializacion perfil on perfil.id=plaesp.especialista_id  where plaesp.planificacionCab_id=@p_placab and  plaesp.frecuencia='ANU' and mes.mes=datepart(MM,plaesp.fechaLimpProf)  and mes.anho=datepart(YYYY,plaesp.fechaLimpProf) FOR JSON PATH) as 'anual'

				
			from #meses mes
END

GO
/****** Object:  StoredProcedure [dbo].[listarSincronizacion]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE    PROCEDURE [dbo].[listarSincronizacion]   
	@mes int,
	@anho int,
	@operario_id int,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		select 
			/*Se envia el primer dia del mes correspondiente a las horas procesadas*/
			cast(cast(sinccab.anho*10000 + sinccab.mes*100 + '01' as varchar(255)) as date) as 'TransDate',
			1 as 'OKFlag',
			op.numCedula as 'PerCode',
			sinccab.nombrePersona as 'PerName',
			(select 
				sincdet.CodUbicacion as 'Location',
				sincdet.tipoHora as 'HourType',
				cast(cast(sincdet.cantidad as float)/cast(60 as float) as decimal(18,2)) as 'Qty'
				from dbo.Operarios_sincronizaciondet sincdet where sincronizacionCab_id=sinccab.id
				FOR JSON AUTO) as 'Math'
			from Operarios_sincronizacioncab sinccab
			inner join dbo.Operarios_operario op on sinccab.operario_id=op.id
			where operario_id=@operario_id and mes=@mes and anho=@anho
			FOR JSON PATH
			
		
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		SET @retorno=1;
		ROLLBACK TRAN @TransactionName; 
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		Select 1 as resultado;
		RETURN 1;
	END CATCH
	Select 0 as resultado;
	RETURN 0;

END	

GO
/****** Object:  StoredProcedure [dbo].[notificacion_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE           PROCEDURE [dbo].[notificacion_trg]   
	@json nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_fechaInicio date;
		declare @fechaCambio datetime;
		DECLARE @p_fechaFin date;
		DECLARE @p_usuario_id int;
		DECLARE @p_planificacionEsp_id int;
		DECLARE @p_fechaUltimaMod datetime2 ;
		DECLARE @p_fechaEnvio datetime2 ;
		DECLARE @p_id int;

		DECLARE @p_userJefe_id int;
		DECLARE @p_userFiscal_id int;
		DECLARE @p_motivo nvarchar(150);
		declare @p_estado nvarchar(30);
		declare @p_cantHorasAprobado nvarchar(8);
		declare @p_cantHorasSolicitado nvarchar(8);
		declare @p_numCantHorasAprobado int;
		declare @p_numCantHorasSolicitado int;
		declare @p_actualizar bit;


		DECLARE @TransactionName varchar(20) = 'Transactional';
		Declare @err_msg nvarchar(max);
		BEGIN TRAN @TransactionName 
		BEGIN TRY
			insert into infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@json);
			select @p_usuario_id="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
			select @p_planificacionEsp_id="value" from OpenJson(@json) where "key"='planificacionEsp_id' and "value"!='None';
			select @p_fechaUltimaMod=convert(datetime,"value",20) from OpenJson(@json) where "key"='fechaUltimaMod' and  "value"!='None' and "value"!='00';
			select @p_fechaEnvio=convert(datetime,"value",20) from OpenJson(@json) where "key"='fechaEnvio' and  "value"!='None' and "value"!='00';
			select @p_id="value" from OpenJson(@json) where "key"='id' and "value"!='None';
			select @p_estado="value" from OpenJson(@json) where "key"='estado' and "value"!='None';
			select @p_cantHorasAprobado="value" from OpenJson(@json) where "key"='cantHorasAprobado' and "value"!='None';
			select @p_numCantHorasAprobado=cast("value" as int) from OpenJson(@json) where "key"='numCantHorasAprobado' and "value"!='None';
			select @p_cantHorasSolicitado="value" from OpenJson(@json) where "key"='cantHorasSolicitado' and "value"!='None';
			select @p_numCantHorasSolicitado=cast("value" as int) from OpenJson(@json) where "key"='numCantHorasSolicitado' and "value"!='None';
			select @p_actualizar="value" from OpenJson(@json) where "key"='actualizarCab' and "value"!='None';
			select @p_motivo="value" from OpenJson(@json) where "key"='motivo' and "value"!='None';
			select @p_userFiscal_id="value" from OpenJson(@json) where "key"='userFiscal_id' and "value"!='None';
			select @p_userJefe_id="value" from OpenJson(@json) where "key"='userJefe_id' and "value"!='None';
		

		
			--select 'termine de castear';
			if @p_fechaUltimaMod is NULL
			begin
				set @p_fechaUltimaMod = CURRENT_TIMESTAMP
			end

			select @p_id=cast("value" as int) from OpenJson(@json) where "key"='id' and "value"!='None';
			if  @p_id is not NULL
			begin
				select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histnotificacion where vactual_id=@p_id;
				if @tmp1_vregistro is NULL
				begin
					set @tmp1_vregistro=1;
					INSERT INTO dbo.Operarios_histnotificacion(usuario_id,planificacionEsp_id,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,userJefe_id ,userFiscal_id ,motivo ,estado ,cantHorasAprobado ,cantHorasSolicitado ,numCantHorasAprobado ,numCantHorasSolicitado,fechaEnvio)
					select usuario_id,planificacionEsp_id,fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_userJefe_id ,@p_userFiscal_id ,@p_motivo ,@p_estado ,@p_cantHorasAprobado ,@p_cantHorasSolicitado ,@p_numCantHorasAprobado ,@p_numCantHorasSolicitado,@p_fechaEnvio from dbo.Operarios_notificacion where id=@p_id;
				end
				update dbo.Operarios_histnotificacion set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro;
				set @tmp1_vregistro=@tmp1_vregistro+1;
				INSERT INTO dbo.Operarios_histnotificacion(usuario_id,planificacionEsp_id,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,userJefe_id ,userFiscal_id ,motivo ,estado ,cantHorasAprobado ,cantHorasSolicitado ,numCantHorasAprobado ,numCantHorasSolicitado,fechaEnvio)
				select @p_usuario_id,@p_planificacionEsp_id,@p_fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_userJefe_id ,@p_userFiscal_id ,@p_motivo ,@p_estado ,@p_cantHorasAprobado ,@p_cantHorasSolicitado ,@p_numCantHorasAprobado ,@p_numCantHorasSolicitado,@p_fechaEnvio
				update dbo.Operarios_notificacion set 
					 usuario_id=@p_usuario_id,
					 planificacionEsp_id=@p_planificacionEsp_id,
					 fechaUltimaMod=@p_fechaUltimaMod,
					 userjefe_id=@p_userJefe_id ,
					 userFiscal_id=@p_userFiscal_id ,
					 motivo=@p_motivo ,
					 estado=@p_estado ,
					 fechaEnvio=@p_fechaEnvio,
					 cantHorasAprobado=@p_cantHorasAprobado ,
					 cantHorasSolicitado=@p_cantHorasSolicitado ,
					 numCantHorasAprobado=@p_numCantHorasAprobado ,
					 numCantHorasSolicitado=@p_numCantHorasSolicitado 
					 where id=@p_id;
				if @p_actualizar ='True'
				begin
					declare @plancab int;
					declare @numNuevaCantHorasCab int;
					declare @nuevaCantHorasCab nvarchar(8);
					declare @numNuevaCantHorasEsp int;
					declare @nuevaCantHorasEsp nvarchar(8);
					declare @veractual int;

					select  @nuevaCantHorasCab="value"  from OpenJson(@json) where "key"='nuevaCantHorasCab' and "value"!='None';
					select  @numNuevaCantHorasCab=cast("value" as int) from OpenJson(@json) where "key"='numNuevaCantHorasCab' and "value"!='None';
					select  @nuevaCantHorasEsp="value" from OpenJson(@json) where "key"='nuevaCantHorasEsp' and "value"!='None';
					select  @numNuevaCantHorasEsp=cast("value" as int) from OpenJson(@json) where "key"='numNuevaCantHorasEsp' and "value"!='None';
				
					select top(1) @plancab=placab.id
					from dbo.Operarios_planificacionesp plaesp
					left join dbo.Operarios_planificacioncab placab on placab.id=plaesp.planificacionCab_id
					where plaesp.id=@p_planificacionEsp_id

					if @plancab is NULL
					begin
						RAISERROR(-15000,0,0,'No hay cabecera')
					end

					select @veractual=max(vregistro) from dbo.Operarios_histplanificacioncab where vactual_id=@plancab;
				
					update dbo.Operarios_planificacioncab set usuario_id=@p_usuario_id,
					cantHorasEsp=@nuevaCantHorasCab,
					numCantHorasEsp=@numNuevaCantHorasCab 
					where id=@plancab;

					update [dbo].[Operarios_histplanificacioncab] set vfechaFin=@fechaCambio,vactual_id=NULL where vactual_id=@plancab and vregistro=@veractual;
					INSERT INTO [dbo].[Operarios_histplanificacioncab]
				   ([fecha]
				   ,[cantidad]
				   ,[cantHoras]
				   ,[cantHorasNoc]
				   ,[cantHorasEsp]
				   ,[rePlanificar]
				   ,[vfechaInicio]
				   ,[vfechaFin]
				   ,[vregistro]
				   ,[puntoServicio_id]
				   ,[vactual_id]
				   ,[usuario_id]
				   ,[numCantHoras]
				   ,[numCantHorasEsp]
				   ,[numCantHorasNoc])
					select
				   [fecha]
				   ,[cantidad]
				   ,[cantHoras]
				   ,[cantHorasNoc]
				   ,[cantHorasEsp]
				   ,[rePlanificar]
				   ,@fechaCambio
				   ,NULL
				   ,@veractual+1
				   ,[puntoServicio_id]
				   ,@plancab
				   ,usuario_id
				   ,[numCantHoras]
				   ,[numCantHorasEsp]
				   ,[numCantHorasNoc] from  [Operarios_histplanificacioncab] where id=@plancab
			
					update dbo.Operarios_histplanificacionope set vfechaFin=@fechaCambio,vactual_id=NULL where planificacionCab_id=@plancab and vfechaFin is NULL and vregistro=@veractual;
					INSERT INTO [dbo].[Operarios_histplanificacionope]
				   ([cantidad]
				   ,[lun]
				   ,[mar]
				   ,[mie]
				   ,[jue]
				   ,[vie]
				   ,[sab]
				   ,[dom]
				   ,[fer]
				   ,[ent]
				   ,[sal]
				   ,[corte]
				   ,[total]
				   ,[vfechaInicio]
				   ,[vfechaFin]
				   ,[vregistro]
				   ,[especialista_id]
				   ,[planificacionCab_id]
				   ,[vactual_id]
				   ,[numTotal])
				   select 
				   [cantidad]
				   ,[lun]
				   ,[mar]
				   ,[mie]
				   ,[jue]
				   ,[vie]
				   ,[sab]
				   ,[dom]
				   ,[fer]
				   ,[ent]
				   ,[sal]
				   ,[corte]
				   ,[total]
				   ,@fechaCambio
				   ,NULL
				   ,@veractual+1
				   ,[especialista_id]
				   ,[planificacionCab_id]
				   ,id
				   ,[numTotal] from [dbo].[Operarios_planificacionope] where planificacionCab_id=@plancab

				   update dbo.Operarios_histplanificacionesp 
					set vfechaFin=@fechaCambio,vactual_id=NULL 
					where 
						planificacionCab_id=@plancab and
						vfechaFin is NULL and 
						vregistro=@veractual;

				   update dbo.Operarios_planificacionesp set numCantHoras=@numNuevaCantHorasEsp,cantHoras=@nuevaCantHorasEsp
				   where id=@p_planificacionEsp_id;
				   INSERT INTO [dbo].[Operarios_histplanificacionesp]
					   ([frecuencia]
					   ,[cantHoras]
					   ,[fechaLimpProf]
					   ,[vfechaInicio]
					   ,[vfechaFin]
					   ,[vregistro]
					   ,[especialista_id]
					   ,[planificacionCab_id]
					   ,[tipo_id]
					   ,[vactual_id]
					   ,[numCantHoras]
					   ,[estado]
					   ,[area]
					   ,[cantidad]
					   ,[sector]
					   ,[tipoHora_id])
				SELECT 
				  [frecuencia]
				  ,cantHoras
				  ,[fechaLimpProf]
				  ,@fechaCambio
				  ,NULL
				  ,@veractual+1
				  ,[especialista_id]
				  ,[planificacionCab_id]
				  ,[tipo_id]
				  ,id
				  ,numCantHoras
				  ,[estado]
				  ,[area]
				  ,[cantidad]
				  ,[sector]
				  ,[tipoHora_id]
					FROM [dbo].[Operarios_planificacionesp] where planificacionCab_id=@plancab;

					end





			end
			if  @p_id is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_notificacion(usuario_id,planificacionEsp_id,fechaUltimaMod,userJefe_id ,userFiscal_id ,motivo ,estado ,cantHorasAprobado ,cantHorasSolicitado ,numCantHorasAprobado ,numCantHorasSolicitado,fechaEnvio)
				select @p_usuario_id,@p_planificacionEsp_id,@p_fechaUltimaMod,@p_userJefe_id ,@p_userFiscal_id ,@p_motivo ,@p_estado ,@p_cantHorasAprobado ,@p_cantHorasSolicitado ,@p_numCantHorasAprobado ,@p_numCantHorasSolicitado,@p_fechaEnvio;
				set @p_id=SCOPE_IDENTITY();
				INSERT INTO dbo.Operarios_histnotificacion(usuario_id,planificacionEsp_id,fechaUltimaMod,vfechaInicio,vfechaFin,vregistro,vactual_id,userJefe_id ,userFiscal_id ,motivo ,estado ,cantHorasAprobado ,cantHorasSolicitado ,numCantHorasAprobado ,numCantHorasSolicitado,fechaEnvio)
				select @p_usuario_id,@p_planificacionEsp_id,@p_fechaUltimaMod,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_userJefe_id ,@p_userFiscal_id ,@p_motivo ,@p_estado ,@p_cantHorasAprobado ,@p_cantHorasSolicitado ,@p_numCantHorasAprobado ,@p_numCantHorasSolicitado,@p_fechaEnvio
			end
			COMMIT TRANSACTION @TransactionName;
		END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		SET @retorno=1;
		ROLLBACK TRAN @TransactionName; 
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@json);
		Select 1 as resultado;
		RETURN 1;
	END CATCH
	Select 0 as resultado;
	RETURN 0;
		

END
GO
/****** Object:  StoredProcedure [dbo].[operario_horario]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE     PROCEDURE [dbo].[operario_horario]   
  
	@asignacion int,   
    @fechaHoraAlerta nvarchar(30)
	--@operario int
AS   
	
    BEGIN
	SET NOCOUNT ON
	/**obtener la asignacion**/
	DECLARE @diaAlerta nvarchar(MAX)
	DECLARE @diaEntrada nvarchar(6)
	DECLARE @diaSalida nvarchar(6)
	DECLARE @horaEntrada time(7)
	DECLARE @horaSalida time(7)
	DECLARE @txtsql1 nvarchar(1000)
	DECLARE @txtsql2 nvarchar(1000)
	DECLARE @fecha date=convert(date,@fechaHoraAlerta)
	DECLARE @operario int
	DECLARE @T1_HORARIOS TABLE (idOrden int identity(1,1) primary key,diaEntrada nvarchar(10), horaEntrada time, diaSalida nvarchar(10), horaSalida time, totalHoras time)

	DECLARE @tiempoDiff time

	SET @tiempoDiff='00:00:00'

	SELECT @diaAlerta=cast(FORMAT(@fecha,'dddd','es-es') as nvarchar)
	

	/**tenemos el dia de entrada que falta**/
	SET @diaEntrada=replace(concat(SUBSTRING(@diaAlerta, 1, 3),'Ent'),'é', 'e')  
	SET @diaEntrada=replace(concat(SUBSTRING(@diaEntrada, 1, 3),'Ent'),'á', 'a')
	SET @diaSalida=replace(concat(SUBSTRING(@diaAlerta, 1, 3),'Sal'), 'é', 'e') 
	SET @diaSalida=replace(concat(SUBSTRING(@diaSalida, 1, 3),'Sal'), 'á', 'a') 

	

	SELECT @operario=operario_id FROM Operarios_asignaciondet WHERE id=@asignacion

	--SET @txtsql1=N'SELECT '+@diaEntrada+' as diaEntrada,'+@diaEntrada+','+@diaSalida+' as diaSalida, '+ @diaSalida+ ' FROM Operarios_asignaciondet  
	--WHERE id='+cast(@asignacion as nvarchar)
	

	INSERT INTO @T1_HORARIOS (diaEntrada, horaEntrada, diaSalida, horaSalida, totalHoras)
	SELECT x.diaEntrada,x.horaEntrada, x.diaSalida, x.horaSalida, DATEADD(second, DATEDIFF(second,x.horaEntrada ,x.horaSalida), @tiempoDiff) as totalHoras FROM (
	SELECT @diaEntrada AS diaEntrada,
	CASE
	WHEN @diaEntrada ='lunEnt' Then  lunEnt 
	WHEN @diaEntrada ='marEnt' Then  marEnt
	WHEN @diaEntrada ='mieEnt' Then  mieEnt
	WHEN @diaEntrada ='jueEnt' Then  jueEnt
	WHEN @diaEntrada ='vieEnt' Then  vieEnt
	WHEN @diaEntrada ='sabEnt' Then  sabEnt
	WHEN @diaEntrada ='domEnt' Then  domEnt
	END as horaEntrada, 
	 @diaSalida AS diaSalida,
	CASE
	WHEN @diaEntrada ='lunEnt' Then  lunSal
	WHEN @diaEntrada ='marEnt' Then  marSal
	WHEN @diaEntrada ='mieEnt' Then  mieSal
	WHEN @diaEntrada ='jueEnt' Then  jueSal
	WHEN @diaEntrada ='vieEnt' Then  vieSal
	WHEN @diaEntrada ='sabEnt' Then  sabSal
	WHEN @diaEntrada ='domEnt' Then  domSal
	END as horaSalida
	FROM Operarios_asignaciondet
	WHERE id=@asignacion) x
	
	--INSERT INTO @T1_HORARIOS (diaEntrada, horaEntrada, diaSalida, horaSalida)
	
	--execute(@txtsql1)
	


	--INSERT INTO @T1_HORARIOS (HoraEntrada, HoraSalida)
	


	SELECT  @horaSalida=horaSalida FROM @T1_HORARIOS

	

	INSERT INTO @T1_HORARIOS (diaEntrada, horaEntrada, diaSalida, horaSalida, totalHoras)
	/**procedemos a calcular la proxima marcacion**/
	SELECT TOP 1 x.*, DATEADD(second, DATEDIFF(second,x.horaEntrada ,x.horaSalida), @tiempoDiff) as totalHoras FROM (
	SELECT @diaEntrada AS diaEntrada,
	CASE
	WHEN @diaEntrada ='lunEnt' Then  lunEnt 
	WHEN @diaEntrada ='marEnt' Then  marEnt
	WHEN @diaEntrada ='mieEnt' Then  mieEnt
	WHEN @diaEntrada ='jueEnt' Then  jueEnt
	WHEN @diaEntrada ='vieEnt' Then  vieEnt
	WHEN @diaEntrada ='sabEnt' Then  sabEnt
	WHEN @diaEntrada ='domEnt' Then  domEnt
	END as horaEntrada, 
	 @diaSalida AS diaSalida,
	CASE
	WHEN @diaEntrada ='lunEnt' Then  lunSal
	WHEN @diaEntrada ='marEnt' Then  marSal
	WHEN @diaEntrada ='mieEnt' Then  mieSal
	WHEN @diaEntrada ='jueEnt' Then  jueSal
	WHEN @diaEntrada ='vieEnt' Then  vieSal
	WHEN @diaEntrada ='sabEnt' Then  sabSal
	WHEN @diaEntrada ='domEnt' Then  domSal
	END as horaSalida
	FROM Operarios_asignaciondet
	WHERE id!=@asignacion AND operario_id=@operario
	AND @fecha>=fechaInicio and (@fecha<=fechaFin or fechaFin is null)) as x
	WHERE  x.horaEntrada>=@horaSalida
	ORDER BY x.horaEntrada asc
	
	
	/**procedemos a obtener la proxima marcacion, obtenemos el operario**/
	
	
	
	select * FROM @T1_HORARIOS

	



		

	END
GO
/****** Object:  StoredProcedure [dbo].[operarios_disponibles]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE     PROCEDURE [dbo].[operarios_disponibles]  
	@puntoServicio int,   
    @totalHoras nvarchar(8),
	@lunEntReq time(7),
	@lunSalReq time(7),
	@marEntReq time(7),
	@marSalReq time(7),
	@mierEntReq time(7),
	@mierSalReq time(7),
	@jueEntReq time(7),
	@jueSalReq time(7),
	@vieEntReq time(7),
	@vieSalReq time(7),
	@sabEntReq time(7),
	@sabSalReq time(7),
	@domEntReq time(7),
	@domSalReq time(7), 
	@fechaInicioOperario nvarchar(10)
	
AS
BEGIN
	DECLARE @horasMaximas int
		DECLARE @traslado int
		--auxiliares para el calculo de horas con el traslado para las entradas
		DECLARE @lunEntReqTras time(7)
		DECLARE @marEntReqTras time(7)
		DECLARE @mierEntReqTras time(7)
		DECLARE @jueEntReqTras time(7)
		DECLARE @vieEntReqTras time(7)
		DECLARE @sabEntReqTras time(7)
		DECLARE @domEntReqTras time (7)
		DECLARE @fechaFin date
		
		--obtenemos la cantidad de horas maximas permitidas por semana
		
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
		--obtenemos el tiempo maximo de traslado de un punto a otro
		SELECT @traslado=cast(valor as int)*-1 FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='TIEMPO_TRASLADO'
		
		--hora requeridas que tienen en cuenta el traslado de un PS a otro PS
		SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
		SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
		SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
		SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
		SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
		SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
		SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
		
		/**fecha por defecto infinito**/
		SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		
		SELECT op.* FROM dbo.detalle_lista_operarios op 
			where op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios op
			INNER JOIN Operarios_asignaciondet asd on asd.operario_id=op.id_operario 
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado='Aprobado' 
			WHERE 
				(asd.lunEnt in(@lunEntReqTras, @lunSalReq)) or (asd.lunSal  in(@lunEntReqTras, @lunSalReq)) 
			or (asd.marEnt    in(@marEntReqTras, @marSalReq)) or (asd.marSal   in(@marEntReqTras, @marSalReq))
			or (asd.mieEnt    in (@mierEntReqTras, @mierSalReq)) or (asd.mieSal  in (@mierEntReqTras, @mierSalReq)) 
			or (asd.jueEnt    in (@jueEntReqTras, @jueSalReq)) or (asd.jueSal  in (@jueEntReqTras, @jueSalReq))
			or (asd.vieEnt    in (@vieEntReqTras, @vieSalReq)) or (asd.vieSal  in (@vieEntReqTras, @vieSalReq))
			or (asd.sabEnt    in (@sabEntReqTras, @sabSalReq)) or (asd.sabSal  in (@sabEntReqTras, @sabSalReq))
			or (asd.domEnt    in (@domEntReqTras, @domSalReq)) or (asd.domSal  in (@domEntReqTras, @domSalReq))	
	
			or op.totalHoras+cast(isnull(@totalHoras,0)  as int)>@horasMaximas
			or (@fechaFin>=asd.fechaInicio and (@fechaFin <=asd.fechaFin or asd.fechaFin is null))
			or (convert(date, @fechaInicioOperario, 23)>=asd.fechaInicio and (convert(date, @fechaInicioOperario)<=asd.fechaFin or asd.fechaFin is null))
			or (convert(date, @fechaInicioOperario, 23) <=asd.fechaInicio and (@fechaFin>=asd.fechaFin or asd.fechaFin is NULL))
			) 
	
END
GO
/****** Object:  StoredProcedure [dbo].[operarios_disponibles_banderas]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE    PROCEDURE [dbo].[operarios_disponibles_banderas]   
	@fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@operario int
AS   
    BEGIN
	set nocount on;
		LINENO 0;
		DECLARE @horasMaximas int =0;
		DECLARE @horasTotales int=0;
		DECLARE @fechaFin date;
		DECLARE @fechaInicio date;
		SET @fechaFin=convert(date, @fechaInicioOperario,103)	 
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
		if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaFinOperario,103)	 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END

		CREATE table #semanas (
			inicio datetime,
			fin datetime,
			dias int,
			semana int
		);
		declare @fi datetime;
		select @fi= convert(date,@fechaInicioOperario,103);
		insert into #semanas EXEC[dbo].[partirSemanas]
		@fechaInicio = @fi,
		@fechaFin = @fechaFin;


		select @horasTotales=sum(resum.totalHoras) from (SELECT        op.id AS id_operario, op.ciudad_id AS ciudad, { fn CONCAT({ fn CONCAT(op.nombre, ' ') }, op.apellido) } AS nombres, op.nroLegajo,/* ISNULL(STRING_AGG(ps.NombrePServicio, ', '), '') AS nombres_puntoServicio, */
                                                    /*ISNULL(STRING_AGG(ps.id, ', '), ' ') AS ids_puntoServicio, */
													SUM(CAST(ISNULL(aod.numTotalHoras, 0) AS float)) + 
													SUM(CAST(ISNULL(aodt.numTotalHoras, 0) AS float))+
													SUM(CAST(ISNULL(asdet.numTotalHoras, 0) AS float))+
													SUM(CAST(ISNULL(DATEDIFF(MI,osdet.horaInicio,osdet.horaFin),0) as float))
													AS totalHoras, 
													aod.fechaInicio as fi1,
													aod.fechaFin as ff1,
													osdet.fecha as fi2,
													rempdet.fecha as fi3,
													rempdet.fechaFin as ff3,
													aodt.fechaInicio as fi4,
													aodt.fechaFin as ff4,
													DATEDIFF(year, op.fechaInicio, GETDATE()) AS antiguedad,
													ss.inicio,
													ss.fin,
													ss.dias,
													ss.semana
                          FROM            dbo.Operarios_operario AS op LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondet aod ON op.id = aod.operario_id LEFT OUTER JOIN
													dbo.Operarios_ordenserviciodet osdet on osdet.operario_id=op.id left outer join
													dbo.Operarios_remplazosdet rempdet on rempdet.remplazo_id=op.id left outer join
													dbo.Operarios_asignaciondet  asdet ON rempdet.Asignacion_id=asdet.id LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondettemp  aodt ON op.id = aodt.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_ciudad AS cd ON cd.id = op.ciudad_id
													right outer join #semanas ss on
													 (
													 
													 (ss.semana>= datepart(WW,aod.fechaInicio) and
													 ss.semana<= datepart(WW,aod.fechaFin))

													 or(ss.semana>= datepart(WW,rempdet.fecha) and
													 ss.semana<= datepart(WW,rempdet.fechaFin))

													 OR(ss.semana= datepart(WW,osdet.fecha) )
													 
													 OR(ss.semana>= datepart(WW,aodt.fechaInicio) and
													 ss.semana<= datepart(WW,aodt.fechaFin))
													 
													 )

                          GROUP BY op.id, op.nombre, op.apellido, op.nroLegajo, op.fechaInicio, op.ciudad_id,aod.fechaInicio,aod.fechaFin,osdet.fecha,rempdet.fecha,rempdet.fechaFin,aodt.fechaInicio,
						  aodt.fechaFin,ss.inicio,ss.fin,ss.dias,ss.semana 
						  having op.id=@operario) resum
		select case when @horasMaximas*60>@horasTotales then 'False' else 'True' end as supera,@horasMaximas as limite,@horasTotales as acumulado;
	END
GO
/****** Object:  StoredProcedure [dbo].[operarios_disponibles_remp]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE            PROCEDURE [dbo].[operarios_disponibles_remp]   
    @tipoRemp nvarchar(10),
	@puntoServicio int, 
	@asigCab int, 
	@operarID int, 
    @totalHoras float,
	@lunEntReq time(7),
	@lunSalReq time(7),
	@marEntReq time(7),
	@marSalReq time(7),
	@mierEntReq time(7),
	@mierSalReq time(7),
	@jueEntReq time(7),
	@jueSalReq time(7),
	@vieEntReq time(7),
	@vieSalReq time(7),
	@sabEntReq time(7),
	@sabSalReq time(7),
	@domEntReq time(7),
	@domSalReq time(7), 
	@fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@perfil nvarchar(3)
AS   
    BEGIN

		LINENO 0;
		set nocount on;
		DECLARE @horasMaximas int
		DECLARE @traslado int
		DECLARE @finalQuery nvarchar(max);
		DECLARE @whenClause nvarchar(max);
		DECLARE @lunEntReqTras time(7)
		DECLARE @marEntReqTras time(7)
		DECLARE @mierEntReqTras time(7)
		DECLARE @jueEntReqTras time(7)
		DECLARE @vieEntReqTras time(7)
		DECLARE @sabEntReqTras time(7)
		DECLARE @domEntReqTras time (7)
		DECLARE @fechaFin date
		declare @cuenta int;
		declare @totalConverted float;
		select @totalConverted=@totalHoras;
		--obtenemos la cantidad de horas maximas permitidas por semana
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
		--obtenemos el tiempo maximo de traslado de un punto a otro
		SELECT @traslado=cast(valor as int)*-1 FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='TIEMPO_TRASLADO'
		--hora requeridas que tienen en cuenta el traslado de un PS a otro PS
		SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
		SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
		SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
		SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
		SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
		SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
		SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
		/*if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaFinOperario)	 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END*/
		if  @tipoRemp='unica'  
		BEGIN
			DECLARE @hrm0_lunEnt time;
			DECLARE @hrm0_lunSal time;
			DECLARE @hrm0_marEnt time;
			DECLARE @hrm0_marSal time;
			DECLARE @hrm0_mieEnt time;
			DECLARE @hrm0_mieSal time;
			DECLARE @hrm0_jueEnt time;
			DECLARE @hrm0_jueSal time;
			DECLARE @hrm0_vieEnt time;
			DECLARE @hrm0_vieSal time;
			DECLARE @hrm0_sabEnt time;
			DECLARE @hrm0_sabSal time;
			DECLARE @hrm0_domEnt time;
			DECLARE @hrm0_domSal time;
			DECLARE @hrm0_asignacionCab_id int;
			DECLARE @hrm0_operario_id int;
			DECLARE @hrm0_fechaInicio date;
			DECLARE @hrm0_totalHoras nvarchar(max);
			DECLARE @hrm0_fechaFin date;
			DECLARE @hrm0_supervisor bit;
			DECLARE @hrm0_perfil_id int;
			declare @lunEntReq_txt nvarchar(20);
			declare @lunSalReq_txt nvarchar(20);
			declare @marEntReq_txt nvarchar(20);
			declare @marSalReq_txt nvarchar(20);
			declare @mierEntReq_txt nvarchar(20);
			declare @mierSalReq_txt nvarchar(20);
			declare @jueEntReq_txt nvarchar(20);
			declare @jueSalReq_txt nvarchar(20);
			declare @vieEntReq_txt nvarchar(20);
			declare @vieSalReq_txt nvarchar(20);
			declare @sabEntReq_txt nvarchar(20);
			declare @sabSalReq_txt nvarchar(20);
			declare @domEntReq_txt nvarchar(20);
			declare @domSalReq_txt nvarchar(20);
			declare @lunEntReqTras_txt nvarchar(20);
			declare @marEntReqTras_txt nvarchar(20);
			declare @mierEntReqTras_txt nvarchar(20);
			declare @jueEntReqTras_txt nvarchar(20);
			declare @vieEntReqTras_txt nvarchar(20);
			declare @sabEntReqTras_txt nvarchar(20);
			declare @domEntReqTras_txt nvarchar(20);
			insert into infolog(fechaHora,info) values(CURRENT_TIMESTAMP,'Llegue aca');
			set @whenClause=' 0=1 ';
			Set @finalQuery='
			then ''Sí'' else ''No'' end as tocalibre 
			FROM dbo.detalle_lista_operarios3 op 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			where  op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_asignaciondet asd on asd.operario_id=op.id_operario 
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado=''Aprobado'' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(op.totalHoras+cast(isnull('+ISNULL(convert(varchar,@totalHoras),'NULL')+',0)  as float)>cast(isnull('+ISNULL(convert(varchar,@horasMaximas),'NULL')+',0)  as float)';
			DECLARE cursorIt CURSOR LOCAL FOR SELECT lunEnt,lunSal,marEnt,marSal,mieEnt,mieSal,jueEnt,jueSal,vieEnt,vieSal,sabEnt,sabSal,domEnt,domSal,asignacionCab_id,operario_id,fechaInicio,totalHoras,fechaFin,supervisor,perfil_id FROM dbo.Operarios_asignaciondet where operario_id=@operarID 
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id
			WHILE @@FETCH_STATUS = 0
			BEGIN
				set @lunEntReq= @hrm0_lunEnt;
				set @lunSalReq= @hrm0_lunSal;
				set @marEntReq= @hrm0_marEnt;
				set @marSalReq= @hrm0_marSal;
				set @mierEntReq= @hrm0_mieEnt;
				set @mierSalReq= @hrm0_mieSal;
				set @jueEntReq= @hrm0_jueEnt;
				set @jueSalReq= @hrm0_jueSal;
				set @vieEntReq= @hrm0_vieEnt;
				set @vieSalReq= @hrm0_vieSal;
				set @sabEntReq= @hrm0_sabEnt;
				set @sabSalReq= @hrm0_sabSal;
				set @domEntReq= @hrm0_domEnt;
				set @domSalReq = @hrm0_domSal;
				SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
				SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
				SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
				SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
				SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
				SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
				SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
				select @lunEntReq_txt=convert(varchar,@lunEntReq,24)
				select @lunSalReq_txt=convert(varchar,@lunSalReq,24)
				select @marEntReq_txt=convert(varchar,@marEntReq,24)
				select @marSalReq_txt=convert(varchar,@marSalReq,24)
				select @mierEntReq_txt=convert(varchar,@mierEntReq,24)
				select @mierSalReq_txt=convert(varchar,@mierSalReq,24)
				select @jueEntReq_txt=convert(varchar,@jueEntReq,24)
				select @jueSalReq_txt=convert(varchar,@jueSalReq,24)
				select @vieEntReq_txt=convert(varchar,@vieEntReq,24)
				select @vieSalReq_txt=convert(varchar,@vieSalReq,24)
				select @sabEntReq_txt=convert(varchar,@sabEntReq,24)
				select @sabSalReq_txt=convert(varchar,@sabSalReq,24)
				select @domEntReq_txt=convert(varchar,@domEntReq,24)
				select @domSalReq_txt=convert(varchar,@domSalReq,24)
				select @lunEntReqTras_txt=convert(varchar,@lunEntReqTras,24)
				select @marEntReqTras_txt=convert(varchar,@marEntReqTras,24)
				select @mierEntReqTras_txt=convert(varchar,@mierEntReqTras,24)
				select @jueEntReqTras_txt=convert(varchar,@jueEntReqTras,24)
				select @vieEntReqTras_txt=convert(varchar,@vieEntReqTras,24)
				select @sabEntReqTras_txt=convert(varchar,@sabEntReqTras,24)
				select @domEntReqTras_txt=convert(varchar,@domEntReqTras,24)
				SET @fechaFin=@hrm0_fechaFin;
				select  @fechaInicioOperario=convert(varchar,@hrm0_fechaInicio,23);
				if  @fechaFin is NULL  
				BEGIN
					SET @fechaFin=convert(date, @fechaInicioOperario)	 
				END
				select @fechaFinOperario=convert(varchar,@fechaFin,23);
				set @whenClause=@whenClause+' or (dl.lunEnt between convert(time, '+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (dl.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+',24))
						or (dl.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+' , 24)) or (dl.marSal  between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+',24))
						or (dl.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+', 24)) or (dl.mieSal between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (dl.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.jueSal between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+' , 24))  
						or (dl.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24)) or (dl.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24))
						or (dl.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24)) or (dl.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24))';


				Set @finalQuery=@finalQuery+'or(
						((convert(date, '+  ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23)>=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23) <=asd.fechaFin or asd.fechaFin is null))
						or (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+', 23)>=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+')<=asd.fechaFin or asd.fechaFin is null))
						or (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+', 23) <=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23)>=asd.fechaFin or asd.fechaFin is NULL))
						) 
					AND(
						(asd.lunEnt between convert(time,'+ISNULL(QUOTENAME(@lunEntReqTras_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (asd.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReqTras_txt,''''),'NULL')+',24) and  convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL') +' ,24)) 
						or (asd.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReqTras_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+'  , 24)) or (asd.marSal   between convert(time,'+ISNULL(QUOTENAME(@marEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL') +',24))
						or (asd.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReqTras_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+' , 24)) or (asd.mieSal  between convert(time,'+ISNULL(QUOTENAME(@mierEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (asd.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+'  , 24)) or (asd.jueSal between  convert(time,'+ISNULL(QUOTENAME(@jueEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL') +',24))
						or (asd.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+'  , 24)) or (asd.vieSal  between convert(time,'+ISNULL(QUOTENAME(@vieEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL') +',24))
						or (asd.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+'  , 24)) or (asd.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL') +',24))
						or (asd.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+'  , 24)) or (asd.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL') +',24))
					)'+' /*or (dl.lunEnt between convert(time, '+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (dl.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+',24))
						or (dl.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+' , 24)) or (dl.marSal  between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+',24))
						or (dl.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+', 24)) or (dl.mieSal between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (dl.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.jueSal between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+' , 24))  
						or (dl.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24)) or (dl.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24))
						or (dl.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24)) or (dl.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24))*/
						)'
			
			FETCH NEXT FROM cursorIt INTO @hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id
			END
			SET @finalQuery=@finalQuery+'))';
			SET @finalQuery=@finalQuery+' AND op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_remplazosdet rem on rem.remplazo_id=op.id_operario 
			INNER JOIN Operarios_asignaciondet asd on rem.Asignacion_id=asd.id
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado=''Aprobado'' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(op.totalHoras+cast(isnull('+ISNULL(convert(varchar,@totalHoras),'NULL')+',0)  as float)>cast(isnull('+ISNULL(convert(varchar,@horasMaximas),'NULL')+',0)  as float)';
			
			DECLARE cursorDt CURSOR LOCAL FOR SELECT lunEnt,lunSal,marEnt,marSal,mieEnt,mieSal,jueEnt,jueSal,vieEnt,vieSal,sabEnt,sabSal,domEnt,domSal,asignacionCab_id,operario_id,fechaInicio,totalHoras,dbo.Operarios_remplazosdet.fechaFin,supervisor,perfil_id FROM dbo.Operarios_asignaciondet left join dbo.Operarios_remplazosdet on dbo.Operarios_remplazosdet.Asignacion_id=dbo.Operarios_asignaciondet.id where dbo.Operarios_remplazosdet.remplazo_id=@operarID 
			OPEN cursorDt
			FETCH NEXT FROM cursorDt INTO @hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id
			WHILE @@FETCH_STATUS = 0
			BEGIN
				set @lunEntReq= @hrm0_lunEnt;
				set @lunSalReq= @hrm0_lunSal;
				set @marEntReq= @hrm0_marEnt;
				set @marSalReq= @hrm0_marSal;
				set @mierEntReq= @hrm0_mieEnt;
				set @mierSalReq= @hrm0_mieSal;
				set @jueEntReq= @hrm0_jueEnt;
				set @jueSalReq= @hrm0_jueSal;
				set @vieEntReq= @hrm0_vieEnt;
				set @vieSalReq= @hrm0_vieSal;
				set @sabEntReq= @hrm0_sabEnt;
				set @sabSalReq= @hrm0_sabSal;
				set @domEntReq= @hrm0_domEnt;
				set @domSalReq = @hrm0_domSal;
				SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
				SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
				SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
				SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
				SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
				SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
				SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
				select @lunEntReq_txt=convert(varchar,@lunEntReq,24)
				select @lunSalReq_txt=convert(varchar,@lunSalReq,24)
				select @marEntReq_txt=convert(varchar,@marEntReq,24)
				select @marSalReq_txt=convert(varchar,@marSalReq,24)
				select @mierEntReq_txt=convert(varchar,@mierEntReq,24)
				select @mierSalReq_txt=convert(varchar,@mierSalReq,24)
				select @jueEntReq_txt=convert(varchar,@jueEntReq,24)
				select @jueSalReq_txt=convert(varchar,@jueSalReq,24)
				select @vieEntReq_txt=convert(varchar,@vieEntReq,24)
				select @vieSalReq_txt=convert(varchar,@vieSalReq,24)
				select @sabEntReq_txt=convert(varchar,@sabEntReq,24)
				select @sabSalReq_txt=convert(varchar,@sabSalReq,24)
				select @domEntReq_txt=convert(varchar,@domEntReq,24)
				select @domSalReq_txt=convert(varchar,@domSalReq,24)
				select @lunEntReqTras_txt=convert(varchar,@lunEntReqTras,24)
				select @marEntReqTras_txt=convert(varchar,@marEntReqTras,24)
				select @mierEntReqTras_txt=convert(varchar,@mierEntReqTras,24)
				select @jueEntReqTras_txt=convert(varchar,@jueEntReqTras,24)
				select @vieEntReqTras_txt=convert(varchar,@vieEntReqTras,24)
				select @sabEntReqTras_txt=convert(varchar,@sabEntReqTras,24)
				select @domEntReqTras_txt=convert(varchar,@domEntReqTras,24)
				SET @fechaFin=@hrm0_fechaFin;
				select  @fechaInicioOperario=convert(varchar,@hrm0_fechaInicio,23);
				if  @fechaFin is NULL  
				BEGIN
					SET @fechaFin=convert(date, @fechaInicioOperario)	 
				END
				select @fechaFinOperario=convert(varchar,@fechaFin,23);
				Set @finalQuery=@finalQuery+'or(
						((convert(date, '+  ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23)>=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23) <=asd.fechaFin or asd.fechaFin is null))
						or (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+', 23)>=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+')<=asd.fechaFin or asd.fechaFin is null))
						or (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+', 23) <=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23)>=asd.fechaFin or asd.fechaFin is NULL))
						) 
					AND(
						(asd.lunEnt between convert(time,'+ISNULL(QUOTENAME(@lunEntReqTras_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (asd.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReqTras_txt,''''),'NULL')+',24) and  convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL') +' ,24)) 
						or (asd.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReqTras_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+'  , 24)) or (asd.marSal   between convert(time,'+ISNULL(QUOTENAME(@marEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL') +',24))
						or (asd.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReqTras_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+' , 24)) or (asd.mieSal  between convert(time,'+ISNULL(QUOTENAME(@mierEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (asd.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+'  , 24)) or (asd.jueSal between  convert(time,'+ISNULL(QUOTENAME(@jueEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL') +',24))
						or (asd.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+'  , 24)) or (asd.vieSal  between convert(time,'+ISNULL(QUOTENAME(@vieEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL') +',24))
						or (asd.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+'  , 24)) or (asd.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL') +',24))
						or (asd.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+'  , 24)) or (asd.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL') +',24))
					)'+' /*or (dl.lunEnt between convert(time, '+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (dl.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+',24))
						or (dl.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+' , 24)) or (dl.marSal  between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+',24))
						or (dl.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+', 24)) or (dl.mieSal between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (dl.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.jueSal between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+' , 24))  
						or (dl.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24)) or (dl.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24))
						or (dl.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24)) or (dl.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24))*/
						)'
			
			FETCH NEXT FROM cursorDt INTO @hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id
			END
			select @cuenta=COUNT(dbo.Operarios_asignaciondet.id) FROM dbo.Operarios_asignaciondet left join dbo.Operarios_remplazosdet on dbo.Operarios_remplazosdet.Asignacion_id=dbo.Operarios_asignaciondet.id where dbo.Operarios_remplazosdet.remplazo_id=@operarID;
			if @cuenta<=0
			begin
				SET @finalQuery=@finalQuery+'))';
			end 

		Set @finalQuery=@finalQuery+'AND ((LEN('+@perfil+')>0 and op.ids_perfil like ''%'+@perfil+'%'') or LEN('+@perfil+')=0) ORDER BY op.totalHoras asc, op.nombres asc';
		Set @finalQuery='SELECT op.* ,case when '+@whenClause+' '+@finalQuery;
		insert into infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@finalQuery);
		EXEC(@finalQuery)
		END

		
	END
GO
/****** Object:  StoredProcedure [dbo].[operarios_disponibles_remp2]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE            PROCEDURE [dbo].[operarios_disponibles_remp2]   
    @tipoRemp nvarchar(10),
	@puntoServicio int, 
	@asigCab int, 
	@operarID int, 
    @totalHoras float,
	@lunEntReq time(7),
	@lunSalReq time(7),
	@marEntReq time(7),
	@marSalReq time(7),
	@mierEntReq time(7),
	@mierSalReq time(7),
	@jueEntReq time(7),
	@jueSalReq time(7),
	@vieEntReq time(7),
	@vieSalReq time(7),
	@sabEntReq time(7),
	@sabSalReq time(7),
	@domEntReq time(7),
	@domSalReq time(7), 
	@fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@perfil nvarchar(3)
AS   
    BEGIN
		LINENO 0;
		set nocount on;
		DECLARE @horasMaximas int
		DECLARE @traslado int
		DECLARE @finalQuery nvarchar(max);
		DECLARE @lunEntReqTras time(7)
		DECLARE @marEntReqTras time(7)
		DECLARE @mierEntReqTras time(7)
		DECLARE @jueEntReqTras time(7)
		DECLARE @vieEntReqTras time(7)
		DECLARE @sabEntReqTras time(7)
		DECLARE @domEntReqTras time (7)
		DECLARE @fechaFin date
		declare @cuenta int;
		declare @totalConverted float;
		select @totalConverted=@totalHoras;
		--obtenemos la cantidad de horas maximas permitidas por semana
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
		--obtenemos el tiempo maximo de traslado de un punto a otro
		SELECT @traslado=cast(valor as int)*-1 FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='TIEMPO_TRASLADO'
		--hora requeridas que tienen en cuenta el traslado de un PS a otro PS
		SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
		SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
		SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
		SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
		SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
		SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
		SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
		/*if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaFinOperario)	 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END*/
		if  @tipoRemp='unica'  
		BEGIN
			DECLARE @hrm0_lunEnt time;
			DECLARE @hrm0_lunSal time;
			DECLARE @hrm0_marEnt time;
			DECLARE @hrm0_marSal time;
			DECLARE @hrm0_mieEnt time;
			DECLARE @hrm0_mieSal time;
			DECLARE @hrm0_jueEnt time;
			DECLARE @hrm0_jueSal time;
			DECLARE @hrm0_vieEnt time;
			DECLARE @hrm0_vieSal time;
			DECLARE @hrm0_sabEnt time;
			DECLARE @hrm0_sabSal time;
			DECLARE @hrm0_domEnt time;
			DECLARE @hrm0_domSal time;
			DECLARE @hrm0_asignacionCab_id int;
			DECLARE @hrm0_operario_id int;
			DECLARE @hrm0_fechaInicio date;
			DECLARE @hrm0_totalHoras nvarchar(max);
			DECLARE @hrm0_fechaFin date;
			DECLARE @hrm0_supervisor bit;
			DECLARE @hrm0_perfil_id int;
			declare @lunEntReq_txt nvarchar(20);
			declare @lunSalReq_txt nvarchar(20);
			declare @marEntReq_txt nvarchar(20);
			declare @marSalReq_txt nvarchar(20);
			declare @mierEntReq_txt nvarchar(20);
			declare @mierSalReq_txt nvarchar(20);
			declare @jueEntReq_txt nvarchar(20);
			declare @jueSalReq_txt nvarchar(20);
			declare @vieEntReq_txt nvarchar(20);
			declare @vieSalReq_txt nvarchar(20);
			declare @sabEntReq_txt nvarchar(20);
			declare @sabSalReq_txt nvarchar(20);
			declare @domEntReq_txt nvarchar(20);
			declare @domSalReq_txt nvarchar(20);
			declare @lunEntReqTras_txt nvarchar(20);
			declare @marEntReqTras_txt nvarchar(20);
			declare @mierEntReqTras_txt nvarchar(20);
			declare @jueEntReqTras_txt nvarchar(20);
			declare @vieEntReqTras_txt nvarchar(20);
			declare @sabEntReqTras_txt nvarchar(20);
			declare @domEntReqTras_txt nvarchar(20);
			insert into infolog(fechaHora,info) values(CURRENT_TIMESTAMP,'Llegue aca');
			Set @finalQuery='SELECT op.* FROM dbo.detalle_lista_operarios3 op 
			where  op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_asignaciondet asd on asd.operario_id=op.id_operario 
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado=''Aprobado'' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(op.totalHoras+cast(isnull('+ISNULL(convert(varchar,@totalHoras),'NULL')+',0)  as float)>cast(isnull('+ISNULL(convert(varchar,@horasMaximas),'NULL')+',0)  as float)';
			DECLARE cursorIt CURSOR LOCAL FOR SELECT lunEnt,lunSal,marEnt,marSal,mieEnt,mieSal,jueEnt,jueSal,vieEnt,vieSal,sabEnt,sabSal,domEnt,domSal,asignacionCab_id,operario_id,fechaInicio,totalHoras,fechaFin,supervisor,perfil_id FROM dbo.Operarios_asignaciondet where operario_id=@operarID 
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id
			WHILE @@FETCH_STATUS = 0
			BEGIN
				set @lunEntReq= @hrm0_lunEnt;
				set @lunSalReq= @hrm0_lunSal;
				set @marEntReq= @hrm0_marEnt;
				set @marSalReq= @hrm0_marSal;
				set @mierEntReq= @hrm0_mieEnt;
				set @mierSalReq= @hrm0_mieSal;
				set @jueEntReq= @hrm0_jueEnt;
				set @jueSalReq= @hrm0_jueSal;
				set @vieEntReq= @hrm0_vieEnt;
				set @vieSalReq= @hrm0_vieSal;
				set @sabEntReq= @hrm0_sabEnt;
				set @sabSalReq= @hrm0_sabSal;
				set @domEntReq= @hrm0_domEnt;
				set @domSalReq = @hrm0_domSal;
				SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
				SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
				SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
				SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
				SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
				SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
				SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
				select @lunEntReq_txt=convert(varchar,@lunEntReq,24)
				select @lunSalReq_txt=convert(varchar,@lunSalReq,24)
				select @marEntReq_txt=convert(varchar,@marEntReq,24)
				select @marSalReq_txt=convert(varchar,@marSalReq,24)
				select @mierEntReq_txt=convert(varchar,@mierEntReq,24)
				select @mierSalReq_txt=convert(varchar,@mierSalReq,24)
				select @jueEntReq_txt=convert(varchar,@jueEntReq,24)
				select @jueSalReq_txt=convert(varchar,@jueSalReq,24)
				select @vieEntReq_txt=convert(varchar,@vieEntReq,24)
				select @vieSalReq_txt=convert(varchar,@vieSalReq,24)
				select @sabEntReq_txt=convert(varchar,@sabEntReq,24)
				select @sabSalReq_txt=convert(varchar,@sabSalReq,24)
				select @domEntReq_txt=convert(varchar,@domEntReq,24)
				select @domSalReq_txt=convert(varchar,@domSalReq,24)
				select @lunEntReqTras_txt=convert(varchar,@lunEntReqTras,24)
				select @marEntReqTras_txt=convert(varchar,@marEntReqTras,24)
				select @mierEntReqTras_txt=convert(varchar,@mierEntReqTras,24)
				select @jueEntReqTras_txt=convert(varchar,@jueEntReqTras,24)
				select @vieEntReqTras_txt=convert(varchar,@vieEntReqTras,24)
				select @sabEntReqTras_txt=convert(varchar,@sabEntReqTras,24)
				select @domEntReqTras_txt=convert(varchar,@domEntReqTras,24)
				SET @fechaFin=@hrm0_fechaFin;
				select  @fechaInicioOperario=convert(varchar,@hrm0_fechaInicio,23);
				if  @fechaFin is NULL  
				BEGIN
					SET @fechaFin=convert(date, @fechaInicioOperario)	 
				END
				select @fechaFinOperario=convert(varchar,@fechaFin,23);
				Set @finalQuery=@finalQuery+'or(
						((convert(date, '+  ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23)>=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23) <=asd.fechaFin or asd.fechaFin is null))
						or (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+', 23)>=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+')<=asd.fechaFin or asd.fechaFin is null))
						or (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+', 23) <=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23)>=asd.fechaFin or asd.fechaFin is NULL))
						) 
					AND(
						(asd.lunEnt between convert(time,'+ISNULL(QUOTENAME(@lunEntReqTras_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (asd.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReqTras_txt,''''),'NULL')+',24) and  convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL') +' ,24)) 
						or (asd.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReqTras_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+'  , 24)) or (asd.marSal   between convert(time,'+ISNULL(QUOTENAME(@marEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL') +',24))
						or (asd.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReqTras_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+' , 24)) or (asd.mieSal  between convert(time,'+ISNULL(QUOTENAME(@mierEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (asd.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+'  , 24)) or (asd.jueSal between  convert(time,'+ISNULL(QUOTENAME(@jueEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL') +',24))
						or (asd.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+'  , 24)) or (asd.vieSal  between convert(time,'+ISNULL(QUOTENAME(@vieEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL') +',24))
						or (asd.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+'  , 24)) or (asd.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL') +',24))
						or (asd.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+'  , 24)) or (asd.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL') +',24))
					)'+' or (dl.lunEnt between convert(time, '+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (dl.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+',24))
						or (dl.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+' , 24)) or (dl.marSal  between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+',24))
						or (dl.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+', 24)) or (dl.mieSal between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (dl.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.jueSal between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+' , 24))  
						or (dl.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24)) or (dl.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24))
						or (dl.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24)) or (dl.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24))
						)'
			
			FETCH NEXT FROM cursorIt INTO @hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id
			END
			SET @finalQuery=@finalQuery+'))';
			SET @finalQuery=@finalQuery+' AND op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_remplazosdet rem on rem.remplazo_id=op.id_operario 
			INNER JOIN Operarios_asignaciondet asd on rem.Asignacion_id=asd.id
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado=''Aprobado'' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(op.totalHoras+cast(isnull('+ISNULL(convert(varchar,@totalHoras),'NULL')+',0)  as float)>cast(isnull('+ISNULL(convert(varchar,@horasMaximas),'NULL')+',0)  as float)';
			
			DECLARE cursorDt CURSOR LOCAL FOR SELECT lunEnt,lunSal,marEnt,marSal,mieEnt,mieSal,jueEnt,jueSal,vieEnt,vieSal,sabEnt,sabSal,domEnt,domSal,asignacionCab_id,operario_id,fechaInicio,totalHoras,dbo.Operarios_remplazosdet.fechaFin,supervisor,perfil_id FROM dbo.Operarios_asignaciondet left join dbo.Operarios_remplazosdet on dbo.Operarios_remplazosdet.Asignacion_id=dbo.Operarios_asignaciondet.id where dbo.Operarios_remplazosdet.remplazo_id=@operarID 
			OPEN cursorDt
			FETCH NEXT FROM cursorDt INTO @hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id
			WHILE @@FETCH_STATUS = 0
			BEGIN
				set @lunEntReq= @hrm0_lunEnt;
				set @lunSalReq= @hrm0_lunSal;
				set @marEntReq= @hrm0_marEnt;
				set @marSalReq= @hrm0_marSal;
				set @mierEntReq= @hrm0_mieEnt;
				set @mierSalReq= @hrm0_mieSal;
				set @jueEntReq= @hrm0_jueEnt;
				set @jueSalReq= @hrm0_jueSal;
				set @vieEntReq= @hrm0_vieEnt;
				set @vieSalReq= @hrm0_vieSal;
				set @sabEntReq= @hrm0_sabEnt;
				set @sabSalReq= @hrm0_sabSal;
				set @domEntReq= @hrm0_domEnt;
				set @domSalReq = @hrm0_domSal;
				SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
				SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
				SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
				SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
				SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
				SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
				SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
				select @lunEntReq_txt=convert(varchar,@lunEntReq,24)
				select @lunSalReq_txt=convert(varchar,@lunSalReq,24)
				select @marEntReq_txt=convert(varchar,@marEntReq,24)
				select @marSalReq_txt=convert(varchar,@marSalReq,24)
				select @mierEntReq_txt=convert(varchar,@mierEntReq,24)
				select @mierSalReq_txt=convert(varchar,@mierSalReq,24)
				select @jueEntReq_txt=convert(varchar,@jueEntReq,24)
				select @jueSalReq_txt=convert(varchar,@jueSalReq,24)
				select @vieEntReq_txt=convert(varchar,@vieEntReq,24)
				select @vieSalReq_txt=convert(varchar,@vieSalReq,24)
				select @sabEntReq_txt=convert(varchar,@sabEntReq,24)
				select @sabSalReq_txt=convert(varchar,@sabSalReq,24)
				select @domEntReq_txt=convert(varchar,@domEntReq,24)
				select @domSalReq_txt=convert(varchar,@domSalReq,24)
				select @lunEntReqTras_txt=convert(varchar,@lunEntReqTras,24)
				select @marEntReqTras_txt=convert(varchar,@marEntReqTras,24)
				select @mierEntReqTras_txt=convert(varchar,@mierEntReqTras,24)
				select @jueEntReqTras_txt=convert(varchar,@jueEntReqTras,24)
				select @vieEntReqTras_txt=convert(varchar,@vieEntReqTras,24)
				select @sabEntReqTras_txt=convert(varchar,@sabEntReqTras,24)
				select @domEntReqTras_txt=convert(varchar,@domEntReqTras,24)
				SET @fechaFin=@hrm0_fechaFin;
				select  @fechaInicioOperario=convert(varchar,@hrm0_fechaInicio,23);
				if  @fechaFin is NULL  
				BEGIN
					SET @fechaFin=convert(date, @fechaInicioOperario)	 
				END
				select @fechaFinOperario=convert(varchar,@fechaFin,23);
				Set @finalQuery=@finalQuery+'or(
						((convert(date, '+  ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23)>=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23) <=asd.fechaFin or asd.fechaFin is null))
						or (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+', 23)>=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+')<=asd.fechaFin or asd.fechaFin is null))
						or (convert(date, '+ISNULL(QUOTENAME(@fechaInicioOperario,''''),'NULL')+', 23) <=asd.fechaInicio and (convert(date, '+ISNULL(QUOTENAME(@fechaFinOperario,''''),'NULL')+', 23)>=asd.fechaFin or asd.fechaFin is NULL))
						) 
					AND(
						(asd.lunEnt between convert(time,'+ISNULL(QUOTENAME(@lunEntReqTras_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (asd.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReqTras_txt,''''),'NULL')+',24) and  convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL') +' ,24)) 
						or (asd.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReqTras_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+'  , 24)) or (asd.marSal   between convert(time,'+ISNULL(QUOTENAME(@marEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL') +',24))
						or (asd.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReqTras_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+' , 24)) or (asd.mieSal  between convert(time,'+ISNULL(QUOTENAME(@mierEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (asd.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+'  , 24)) or (asd.jueSal between  convert(time,'+ISNULL(QUOTENAME(@jueEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL') +',24))
						or (asd.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+'  , 24)) or (asd.vieSal  between convert(time,'+ISNULL(QUOTENAME(@vieEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL') +',24))
						or (asd.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+'  , 24)) or (asd.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL') +',24))
						or (asd.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReqTras_txt,''''),'NULL')+', 24)	and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+'  , 24)) or (asd.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReqTras_txt,''''),'NULL')+',24) and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL') +',24))
					)'+' or (dl.lunEnt between convert(time, '+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+'  , 24)) or (dl.lunSal  between convert(time,'+ISNULL(QUOTENAME(@lunEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@lunSalReq_txt,''''),'NULL')+',24))
						or (dl.marEnt between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+' , 24)) or (dl.marSal  between convert(time,'+ISNULL(QUOTENAME(@marEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@marSalReq_txt,''''),'NULL')+',24))
						or (dl.mieEnt between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24)and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+', 24)) or (dl.mieSal between convert(time,'+ISNULL(QUOTENAME(@mierEntReq_txt,''''),'NULL')+', 24) and convert(time,'+ISNULL(QUOTENAME(@mierSalReq_txt,''''),'NULL')+',24))
						or (dl.jueEnt between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.jueSal between convert(time,'+ISNULL(QUOTENAME(@jueEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@jueSalReq_txt,''''),'NULL')+' , 24))
						or (dl.vieEnt between convert(time,'+ISNULL(QUOTENAME(@vieEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@vieSalReq_txt,''''),'NULL')+' , 24))  
						or (dl.sabEnt between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24)) or (dl.sabSal  between convert(time,'+ISNULL(QUOTENAME(@sabEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@sabSalReq_txt,''''),'NULL')+' , 24))
						or (dl.domEnt between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+' , 24)and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24)) or (dl.domSal  between convert(time,'+ISNULL(QUOTENAME(@domEntReq_txt,''''),'NULL')+') and convert(time,'+ISNULL(QUOTENAME(@domSalReq_txt,''''),'NULL')+' , 24))
						)'
			
			FETCH NEXT FROM cursorDt INTO @hrm0_lunEnt,@hrm0_lunSal,@hrm0_marEnt,@hrm0_marSal,@hrm0_mieEnt,@hrm0_mieSal,@hrm0_jueEnt,@hrm0_jueSal,@hrm0_vieEnt,@hrm0_vieSal,@hrm0_sabEnt,@hrm0_sabSal,@hrm0_domEnt,@hrm0_domSal,@hrm0_asignacionCab_id,@hrm0_operario_id,@hrm0_fechaInicio,@hrm0_totalHoras,@hrm0_fechaFin,@hrm0_supervisor,@hrm0_perfil_id
			END
			select @cuenta=COUNT(dbo.Operarios_asignaciondet.id) FROM dbo.Operarios_asignaciondet left join dbo.Operarios_remplazosdet on dbo.Operarios_remplazosdet.Asignacion_id=dbo.Operarios_asignaciondet.id where dbo.Operarios_remplazosdet.remplazo_id=@operarID;
			if @cuenta<=0
			begin
				SET @finalQuery=@finalQuery+'))';
			end 

		Set @finalQuery=@finalQuery+'AND ((LEN('+@perfil+')>0 and op.ids_perfil like ''%'+@perfil+'%'') or LEN('+@perfil+')=0) ORDER BY op.totalHoras asc, op.nombres asc';
		insert into infolog(fechaHora,info) values(CURRENT_TIMESTAMP,@finalQuery);
		EXEC(@finalQuery)
		END

		
	END
GO
/****** Object:  StoredProcedure [dbo].[operarios_disponibles_v2]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE     PROCEDURE [dbo].[operarios_disponibles_v2]   
    @puntoServicio int,   
    @totalHoras nvarchar(8),
	@lunEntReq time(7),
	@lunSalReq time(7),
	@marEntReq time(7),
	@marSalReq time(7),
	@mierEntReq time(7),
	@mierSalReq time(7),
	@jueEntReq time(7),
	@jueSalReq time(7),
	@vieEntReq time(7),
	@vieSalReq time(7),
	@sabEntReq time(7),
	@sabSalReq time(7),
	@domEntReq time(7),
	@domSalReq time(7), 
	@fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@perfil nvarchar(3)
	
AS   

    BEGIN
		DECLARE @horasMaximas int
		DECLARE @traslado int
		--auxiliares para el calculo de horas con el traslado para las entradas
		DECLARE @lunEntReqTras time(7)
		DECLARE @marEntReqTras time(7)
		DECLARE @mierEntReqTras time(7)
		DECLARE @jueEntReqTras time(7)
		DECLARE @vieEntReqTras time(7)
		DECLARE @sabEntReqTras time(7)
		DECLARE @domEntReqTras time (7)
		DECLARE @fechaFin date
		
		--obtenemos la cantidad de horas maximas permitidas por semana
		
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
		--obtenemos el tiempo maximo de traslado de un punto a otro
		SELECT @traslado=cast(valor as int)*-1 FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='TIEMPO_TRASLADO'
		
		--hora requeridas que tienen en cuenta el traslado de un PS a otro PS
		SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
		SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
		SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
		SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
		SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
		SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
		SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
		
		if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaInicioOperario)
				 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END
		SELECT op.* FROM dbo.detalle_lista_operarios op 
			where op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios op
			INNER JOIN Operarios_asignaciondet asd on asd.operario_id=op.id_operario 
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado='Aprobado' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(asd.lunEnt between @lunEntReqTras and @lunSalReq) or (asd.lunSal  between @lunEntReqTras and @lunSalReq) 
			or (asd.marEnt between @marEntReqTras and @marSalReq) or (asd.marSal   between @marEntReqTras and @marSalReq)
			or (asd.mieEnt between @mierEntReqTras and @mierSalReq) or (asd.mieSal  between @mierEntReqTras and @mierSalReq)
			or (asd.jueEnt between @jueEntReqTras and @jueSalReq) or (asd.jueSal between @jueEntReqTras and  @jueSalReq)
			or (asd.vieEnt between @vieEntReqTras and @vieSalReq) or (asd.vieSal  between  @vieEntReqTras and @vieSalReq)
			or (asd.sabEnt between @sabEntReqTras and @sabSalReq) or (asd.sabSal  between @sabEntReqTras and @sabSalReq)
			or (asd.domEnt between @domEntReqTras and @domSalReq) or (asd.domSal  between @domEntReqTras and @domSalReq)	
	
			or op.totalHoras+cast(isnull(@totalHoras,0)  as int)>@horasMaximas
			or (@fechaFin>=asd.fechaInicio and (@fechaFin <=asd.fechaFin or asd.fechaFin is null))
			or (convert(date, @fechaInicioOperario, 23)>=asd.fechaInicio and (convert(date, @fechaInicioOperario)<=asd.fechaFin or asd.fechaFin is null))
			or (convert(date, @fechaInicioOperario, 23) <=asd.fechaInicio and (@fechaFin>=asd.fechaFin or asd.fechaFin is NULL))
			/**traemos los que tienen dia libre en ese dia del requerimiento**/
			or (dl.lunEnt between @lunEntReq and @lunSalReq) or (dl.lunSal between @lunEntReq and @lunSalReq)
			or (dl.marEnt between @marEntReq and @marSalReq) or (dl.marSal between @marEntReqTras and @marSalReq)
			or (dl.mieEnt between @mierEntReq and @mierSalReq) or (dl.mieSal  between @mierEntReq and @mierSalReq)
			or (dl.jueEnt between  @jueEntReq and @jueSalReq)
			or (dl.jueSal between  @jueEntReq and @jueSalReq)
			or (dl.vieEnt between  @vieEntReq and @vieSalReq)  
			or (dl.sabEnt between @sabEntReq and @sabSalReq) or (dl.sabSal  between @sabEntReq and @sabSalReq)
			or (dl.domEnt  between @domEntReq and @domSalReq) or (dl.domSal  between @domEntReq and @domSalReq)

			
			
						) 
		AND ((LEN(@perfil)>0 and op.ids_perfil like '%'+@perfil+'%') or LEN(@perfil)=0)
		ORDER BY op.totalHoras asc, op.nombres asc

	END
GO
/****** Object:  StoredProcedure [dbo].[operarios_disponibles_v3]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE          PROCEDURE [dbo].[operarios_disponibles_v3]   
    @puntoServicio int,   
    @totalHoras float,
	@lunEntReq time(7),
	@lunSalReq time(7),
	@marEntReq time(7),
	@marSalReq time(7),
	@mierEntReq time(7),
	@mierSalReq time(7),
	@jueEntReq time(7),
	@jueSalReq time(7),
	@vieEntReq time(7),
	@vieSalReq time(7),
	@sabEntReq time(7),
	@sabSalReq time(7),
	@domEntReq time(7),
	@domSalReq time(7), 
	@fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@perfil nvarchar(3)
AS   
    BEGIN
		LINENO 0;
		DECLARE @horasMaximas int
		DECLARE @traslado int
		DECLARE @lunEntReqTras time(7)
		DECLARE @marEntReqTras time(7)
		DECLARE @mierEntReqTras time(7)
		DECLARE @jueEntReqTras time(7)
		DECLARE @vieEntReqTras time(7)
		DECLARE @sabEntReqTras time(7)
		DECLARE @domEntReqTras time (7)
		DECLARE @fechaFin date
		declare @totalConverted float;
		select @totalConverted=@totalHoras;
		--obtenemos la cantidad de horas maximas permitidas por semana
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
		--obtenemos el tiempo maximo de traslado de un punto a otro
		SELECT @traslado=cast(valor as int)*-1 FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='TIEMPO_TRASLADO'
		--hora requeridas que tienen en cuenta el traslado de un PS a otro PS
		SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
		SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
		SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
		SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
		SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
		SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
		SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
		if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaFinOperario)	 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END
		SELECT op.*,case when (dl.lunEnt between @lunEntReq and @lunSalReq) 
			or (dl.lunSal between @lunEntReq and @lunSalReq)
			or (dl.marEnt between @marEntReq and @marSalReq) 
			or (dl.marSal between @marEntReqTras and @marSalReq)
			or (dl.mieEnt between @mierEntReq and @mierSalReq) 
			or (dl.mieSal  between @mierEntReq and @mierSalReq)
			or (dl.jueEnt between  @jueEntReq and @jueSalReq)
			or (dl.jueSal between  @jueEntReq and @jueSalReq)
			or (dl.vieEnt between  @vieEntReq and @vieSalReq)  
			or (dl.sabEnt between @sabEntReq and @sabSalReq) 
			or (dl.sabSal  between @sabEntReq and @sabSalReq)
			or (dl.domEnt  between @domEntReq and @domSalReq) 
			or (dl.domSal  between @domEntReq and @domSalReq)
			then 'Sí' else 'No' end as tocalibre
			FROM dbo.detalle_lista_operarios3 op 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario

			where  op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_asignaciondet asd on asd.operario_id=op.id_operario 
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado='Aprobado' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(
			
			op.totalHoras+cast(isnull(@totalHoras,0)  as float)>@horasMaximas
			
			
			or((
				(@fechaFin>=asd.fechaInicio and (@fechaFin <=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23)>=asd.fechaInicio and (convert(date, @fechaInicioOperario)<=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23) <=asd.fechaInicio and (@fechaFin>=asd.fechaFin or asd.fechaFin is NULL))
				)
			AND(
				(asd.lunEnt between @lunEntReqTras and @lunSalReq) or (asd.lunSal  between @lunEntReqTras and @lunSalReq) 
				or (asd.marEnt between @marEntReqTras and @marSalReq) or (asd.marSal   between @marEntReqTras and @marSalReq)
				or (asd.mieEnt between @mierEntReqTras and @mierSalReq) or (asd.mieSal  between @mierEntReqTras and @mierSalReq)
				or (asd.jueEnt between @jueEntReqTras and @jueSalReq) or (asd.jueSal between @jueEntReqTras and  @jueSalReq)
				or (asd.vieEnt between @vieEntReqTras and @vieSalReq) or (asd.vieSal  between  @vieEntReqTras and @vieSalReq)
				or (asd.sabEnt between @sabEntReqTras and @sabSalReq) or (asd.sabSal  between @sabEntReqTras and @sabSalReq)
				or (asd.domEnt between @domEntReqTras and @domSalReq) or (asd.domSal  between @domEntReqTras and @domSalReq)
			
			))
			
			/**traemos los que tienen dia libre en ese dia del requerimiento**/
			/*or (dl.lunEnt between @lunEntReq and @lunSalReq) or (dl.lunSal between @lunEntReq and @lunSalReq)
			or (dl.marEnt between @marEntReq and @marSalReq) or (dl.marSal between @marEntReqTras and @marSalReq)
			or (dl.mieEnt between @mierEntReq and @mierSalReq) or (dl.mieSal  between @mierEntReq and @mierSalReq)
			or (dl.jueEnt between  @jueEntReq and @jueSalReq)
			or (dl.jueSal between  @jueEntReq and @jueSalReq)
			or (dl.vieEnt between  @vieEntReq and @vieSalReq)  
			or (dl.sabEnt between @sabEntReq and @sabSalReq) or (dl.sabSal  between @sabEntReq and @sabSalReq)
			or (dl.domEnt  between @domEntReq and @domSalReq) or (dl.domSal  between @domEntReq and @domSalReq)*/
			)) AND op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_asignaciondettemp asd on asd.operario_id=op.id_operario 
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado='Aprobado' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(op.totalHoras+cast(isnull(@totalHoras,0)  as float)>@horasMaximas
			
			
			or((
				(@fechaFin>=asd.fechaInicio and (@fechaFin <=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23)>=asd.fechaInicio and (convert(date, @fechaInicioOperario)<=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23) <=asd.fechaInicio and (@fechaFin>=asd.fechaFin or asd.fechaFin is NULL))
				)
			AND(
				(asd.lunEnt between @lunEntReqTras and @lunSalReq) or (asd.lunSal  between @lunEntReqTras and @lunSalReq) 
				or (asd.marEnt between @marEntReqTras and @marSalReq) or (asd.marSal   between @marEntReqTras and @marSalReq)
				or (asd.mieEnt between @mierEntReqTras and @mierSalReq) or (asd.mieSal  between @mierEntReqTras and @mierSalReq)
				or (asd.jueEnt between @jueEntReqTras and @jueSalReq) or (asd.jueSal between @jueEntReqTras and  @jueSalReq)
				or (asd.vieEnt between @vieEntReqTras and @vieSalReq) or (asd.vieSal  between  @vieEntReqTras and @vieSalReq)
				or (asd.sabEnt between @sabEntReqTras and @sabSalReq) or (asd.sabSal  between @sabEntReqTras and @sabSalReq)
				or (asd.domEnt between @domEntReqTras and @domSalReq) or (asd.domSal  between @domEntReqTras and @domSalReq)
			
			))
			
			/**traemos los que tienen dia libre en ese dia del requerimiento
			or (dl.lunEnt between @lunEntReq and @lunSalReq) or (dl.lunSal between @lunEntReq and @lunSalReq)
			or (dl.marEnt between @marEntReq and @marSalReq) or (dl.marSal between @marEntReqTras and @marSalReq)
			or (dl.mieEnt between @mierEntReq and @mierSalReq) or (dl.mieSal  between @mierEntReq and @mierSalReq)
			or (dl.jueEnt between  @jueEntReq and @jueSalReq)
			or (dl.jueSal between  @jueEntReq and @jueSalReq)
			or (dl.vieEnt between  @vieEntReq and @vieSalReq)  
			or (dl.sabEnt between @sabEntReq and @sabSalReq) or (dl.sabSal  between @sabEntReq and @sabSalReq)
			or (dl.domEnt  between @domEntReq and @domSalReq) or (dl.domSal  between @domEntReq and @domSalReq)**/
			)
			) AND op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_remplazosdet rem on rem.remplazo_id=op.id_operario 
			INNER JOIN Operarios_asignaciondet asd on rem.Asignacion_id=asd.id
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado='Aprobado' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(op.totalHoras+cast(isnull(@totalHoras,0)  as float)>@horasMaximas
			
			
			or((
				(@fechaFin>=asd.fechaInicio and (@fechaFin <=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23)>=asd.fechaInicio and (convert(date, @fechaInicioOperario)<=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23) <=asd.fechaInicio and (@fechaFin>=asd.fechaFin or asd.fechaFin is NULL))
				)
			AND(
				(asd.lunEnt between @lunEntReqTras and @lunSalReq) or (asd.lunSal  between @lunEntReqTras and @lunSalReq) 
				or (asd.marEnt between @marEntReqTras and @marSalReq) or (asd.marSal   between @marEntReqTras and @marSalReq)
				or (asd.mieEnt between @mierEntReqTras and @mierSalReq) or (asd.mieSal  between @mierEntReqTras and @mierSalReq)
				or (asd.jueEnt between @jueEntReqTras and @jueSalReq) or (asd.jueSal between @jueEntReqTras and  @jueSalReq)
				or (asd.vieEnt between @vieEntReqTras and @vieSalReq) or (asd.vieSal  between  @vieEntReqTras and @vieSalReq)
				or (asd.sabEnt between @sabEntReqTras and @sabSalReq) or (asd.sabSal  between @sabEntReqTras and @sabSalReq)
				or (asd.domEnt between @domEntReqTras and @domSalReq) or (asd.domSal  between @domEntReqTras and @domSalReq)
			
			))
			
			/**traemos los que tienen dia libre en ese dia del requerimiento**/
			/*or (dl.lunEnt between @lunEntReq and @lunSalReq) or (dl.lunSal between @lunEntReq and @lunSalReq)
			or (dl.marEnt between @marEntReq and @marSalReq) or (dl.marSal between @marEntReqTras and @marSalReq)
			or (dl.mieEnt between @mierEntReq and @mierSalReq) or (dl.mieSal  between @mierEntReq and @mierSalReq)
			or (dl.jueEnt between  @jueEntReq and @jueSalReq)
			or (dl.jueSal between  @jueEntReq and @jueSalReq)
			or (dl.vieEnt between  @vieEntReq and @vieSalReq)  
			or (dl.sabEnt between @sabEntReq and @sabSalReq) or (dl.sabSal  between @sabEntReq and @sabSalReq)
			or (dl.domEnt  between @domEntReq and @domSalReq) or (dl.domSal  between @domEntReq and @domSalReq)*/
			)
			)



		AND ((LEN(@perfil)>0 and op.ids_perfil like '%'+@perfil+'%') or LEN(@perfil)=0)
		ORDER BY op.totalHoras asc, op.nombres asc
	END
GO
/****** Object:  StoredProcedure [dbo].[operarios_disponibles_v4]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[operarios_disponibles_v4]   
    @puntoServicio int,   
    @totalHoras float,
	@lunEntReq time(7),
	@lunSalReq time(7),
	@marEntReq time(7),
	@marSalReq time(7),
	@mierEntReq time(7),
	@mierSalReq time(7),
	@jueEntReq time(7),
	@jueSalReq time(7),
	@vieEntReq time(7),
	@vieSalReq time(7),
	@sabEntReq time(7),
	@sabSalReq time(7),
	@domEntReq time(7),
	@domSalReq time(7), 
	@fechaInicioOperario nvarchar(10),
	@fechaFinOperario nvarchar(10),
	@perfil nvarchar(3)
AS   
    BEGIN
		LINENO 0;
		SET nocount on;
		DECLARE @horasMaximas int
		DECLARE @traslado int
		DECLARE @lunEntReqTras time(7)
		DECLARE @marEntReqTras time(7)
		DECLARE @mierEntReqTras time(7)
		DECLARE @jueEntReqTras time(7)
		DECLARE @vieEntReqTras time(7)
		DECLARE @sabEntReqTras time(7)
		DECLARE @domEntReqTras time (7)
		DECLARE @fechaFin date
		declare @totalConverted float;
		select @totalConverted=@totalHoras;
		--obtenemos la cantidad de horas maximas permitidas por semana
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
		--obtenemos el tiempo maximo de traslado de un punto a otro
		SELECT @traslado=cast(valor as int)*-1 FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='TIEMPO_TRASLADO'
		--hora requeridas que tienen en cuenta el traslado de un PS a otro PS
		SELECT @lunEntReqTras=CAST (DATEADD(MINUTE, @traslado, @lunEntReq) AS TIME)  
		SELECT @marEntReqTras=CAST (DATEADD(MINUTE, @traslado, @marEntReq) AS TIME)
		SELECT @mierEntReqTras=CAST (DATEADD(MINUTE, @traslado, @mierEntReq) AS TIME)
		SELECT @jueEntReqTras=CAST(DATEADD(MINUTE, @traslado, @jueEntReq) AS TIME)
		SELECT @vieEntReqTras=CAST(DATEADD(MINUTE, @traslado, @vieEntReq) AS TIME)
		SELECT @sabEntReqTras=CAST(DATEADD(MINUTE, @traslado, @sabEntReq) AS TIME)
		SELECT @domEntReqTras=CAST(DATEADD(MINUTE, @traslado, @domEntReq) AS TIME)
		CREATE table #semanas (
			inicio datetime,
			fin datetime,
			dias int,
			semana int
		);
	
		if  LEN(@fechaFinOperario)>0  
		BEGIN
			SET @fechaFin=convert(date, @fechaFinOperario)	 
		END
		ELSE 
		BEGIN
			SET @fechaFin=CONVERT(date, '2099-01-01', 23)
		END
		declare @fi datetime;
		select @fi= convert(date,@fechaInicioOperario,23);
		insert into #semanas EXEC[dbo].[partirSemanas]
		@fechaInicio = @fi,
		@fechaFin = @fechaFin;


		SELECT op.*,case when 
			   ( @lunEntReq is not NULL and @lunSalReq is not Null   and dl.lunEnt is not NULL and(@lunEntReq  between dl.lunEnt and dl.lunSal) and (@lunSalReq  between dl.lunEnt and dl.lunSal))	   
			or ( @marEntReq is not NULL and @marSalReq is not Null   and dl.marEnt is not NULL and(@marEntReq  between dl.marEnt and dl.marSal) and (@marSalReq  between dl.marEnt and dl.marSal))
			or ( @mierEntReq is not NULL and @mierSalReq is not Null and dl.mieEnt is not NULL and(@mierEntReq between dl.mieEnt and dl.mieSal) and (@mierSalReq between dl.mieEnt and dl.mieSal)) 
			or ( @jueEntReq is not NULL and @jueSalReq is not Null   and dl.jueEnt is not NULL and( @jueEntReq between dl.jueEnt and dl.jueSal) and (@jueSalReq  between dl.jueEnt and dl.jueSal))   
			or ( @vieEntReq is not NULL and @vieSalReq is not Null   and dl.vieEnt is not NULL and( @vieEntReq between dl.vieEnt and dl.vieSal) and (@vieSalReq  between dl.vieEnt and dl.vieSal))   
			or ( @sabEntReq is not NULL and @sabSalReq is not Null   and dl.sabEnt is not NULL and(@sabEntReq  between dl.sabEnt and dl.sabSal) and (@sabSalReq  between dl.sabEnt and dl.sabSal))   
			or ( @domEntReq is not NULL and @domSalReq is not Null   and dl.domEnt is not NULL and(@domEntReq  between dl.domEnt and dl.domSal) and (@domSalReq  between dl.domEnt and dl.domSal))
			then 'Sí' else 'No' end as tocalibre,
			(SELECT case when  @horasMaximas*60<= SUM(CAST(ISNULL(aod.numTotalHoras, 0) AS float)) + 
													SUM(CAST(ISNULL(aodt.numTotalHoras, 0) AS float))+
													SUM(CAST(ISNULL(asdet.numTotalHoras, 0) AS float))+
													SUM(CAST(ISNULL(DATEDIFF(MI,osdet.horaInicio,osdet.horaFin),0) as float)) then 'True' else 'False' end
													AS superaHoras
                          FROM            dbo.Operarios_operario AS opi LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondet aod ON opi.id = aod.operario_id LEFT OUTER JOIN
													dbo.Operarios_ordenserviciodet osdet on osdet.operario_id=opi.id left outer join
													dbo.Operarios_remplazosdet rempdet on rempdet.remplazo_id=opi.id left outer join
													dbo.Operarios_asignaciondet  asdet ON rempdet.Asignacion_id=asdet.id LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondettemp  aodt ON opi.id = aodt.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_ciudad AS cd ON cd.id = opi.ciudad_id
													right outer join #semanas ss on
													 (
													 
													 (ss.semana>= datepart(WW,aod.fechaInicio) and
													 ss.semana<= datepart(WW,aod.fechaFin))

													 or(ss.semana>= datepart(WW,rempdet.fecha) and
													 ss.semana<= datepart(WW,rempdet.fechaFin))

													 OR(ss.semana= datepart(WW,osdet.fecha) )
													 
													 OR(ss.semana>= datepart(WW,aodt.fechaInicio) and
													 ss.semana<= datepart(WW,aodt.fechaFin))
													 
													 )),
			'False' as otraAsignacion
			FROM dbo.detalle_lista_operarios3 op 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario

			where  op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_asignaciondet asd on asd.operario_id=op.id_operario 
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado='Aprobado' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(
			
			op.totalHoras+cast(isnull(@totalHoras,0)  as float)>@horasMaximas
			
			
			or((
				(@fechaFin>=asd.fechaInicio and (@fechaFin <=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23)>=asd.fechaInicio and (convert(date, @fechaInicioOperario)<=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23) <=asd.fechaInicio and (@fechaFin>=asd.fechaFin or asd.fechaFin is NULL))
				)
			AND(
				(asd.lunEnt between @lunEntReqTras and @lunSalReq) or (asd.lunSal  between @lunEntReqTras and @lunSalReq) 
				or (asd.marEnt between @marEntReqTras and @marSalReq) or (asd.marSal   between @marEntReqTras and @marSalReq)
				or (asd.mieEnt between @mierEntReqTras and @mierSalReq) or (asd.mieSal  between @mierEntReqTras and @mierSalReq)
				or (asd.jueEnt between @jueEntReqTras and @jueSalReq) or (asd.jueSal between @jueEntReqTras and  @jueSalReq)
				or (asd.vieEnt between @vieEntReqTras and @vieSalReq) or (asd.vieSal  between  @vieEntReqTras and @vieSalReq)
				or (asd.sabEnt between @sabEntReqTras and @sabSalReq) or (asd.sabSal  between @sabEntReqTras and @sabSalReq)
				or (asd.domEnt between @domEntReqTras and @domSalReq) or (asd.domSal  between @domEntReqTras and @domSalReq)
			
			))
			
			/**traemos los que tienen dia libre en ese dia del requerimiento**/
			/*or (dl.lunEnt between @lunEntReq and @lunSalReq) or (dl.lunSal between @lunEntReq and @lunSalReq)
			or (dl.marEnt between @marEntReq and @marSalReq) or (dl.marSal between @marEntReqTras and @marSalReq)
			or (dl.mieEnt between @mierEntReq and @mierSalReq) or (dl.mieSal  between @mierEntReq and @mierSalReq)
			or (dl.jueEnt between  @jueEntReq and @jueSalReq)
			or (dl.jueSal between  @jueEntReq and @jueSalReq)
			or (dl.vieEnt between  @vieEntReq and @vieSalReq)  
			or (dl.sabEnt between @sabEntReq and @sabSalReq) or (dl.sabSal  between @sabEntReq and @sabSalReq)
			or (dl.domEnt  between @domEntReq and @domSalReq) or (dl.domSal  between @domEntReq and @domSalReq)*/
			)) AND op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_asignaciondettemp asd on asd.operario_id=op.id_operario 
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado='Aprobado' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(op.totalHoras+cast(isnull(@totalHoras,0)  as float)>@horasMaximas
			
			
			or((
				(@fechaFin>=asd.fechaInicio and (@fechaFin <=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23)>=asd.fechaInicio and (convert(date, @fechaInicioOperario)<=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23) <=asd.fechaInicio and (@fechaFin>=asd.fechaFin or asd.fechaFin is NULL))
				)
			AND(
				(asd.lunEnt between @lunEntReqTras and @lunSalReq) or (asd.lunSal  between @lunEntReqTras and @lunSalReq) 
				or (asd.marEnt between @marEntReqTras and @marSalReq) or (asd.marSal   between @marEntReqTras and @marSalReq)
				or (asd.mieEnt between @mierEntReqTras and @mierSalReq) or (asd.mieSal  between @mierEntReqTras and @mierSalReq)
				or (asd.jueEnt between @jueEntReqTras and @jueSalReq) or (asd.jueSal between @jueEntReqTras and  @jueSalReq)
				or (asd.vieEnt between @vieEntReqTras and @vieSalReq) or (asd.vieSal  between  @vieEntReqTras and @vieSalReq)
				or (asd.sabEnt between @sabEntReqTras and @sabSalReq) or (asd.sabSal  between @sabEntReqTras and @sabSalReq)
				or (asd.domEnt between @domEntReqTras and @domSalReq) or (asd.domSal  between @domEntReqTras and @domSalReq)
			
			))
			
			/**traemos los que tienen dia libre en ese dia del requerimiento
			or (dl.lunEnt between @lunEntReq and @lunSalReq) or (dl.lunSal between @lunEntReq and @lunSalReq)
			or (dl.marEnt between @marEntReq and @marSalReq) or (dl.marSal between @marEntReqTras and @marSalReq)
			or (dl.mieEnt between @mierEntReq and @mierSalReq) or (dl.mieSal  between @mierEntReq and @mierSalReq)
			or (dl.jueEnt between  @jueEntReq and @jueSalReq)
			or (dl.jueSal between  @jueEntReq and @jueSalReq)
			or (dl.vieEnt between  @vieEntReq and @vieSalReq)  
			or (dl.sabEnt between @sabEntReq and @sabSalReq) or (dl.sabSal  between @sabEntReq and @sabSalReq)
			or (dl.domEnt  between @domEntReq and @domSalReq) or (dl.domSal  between @domEntReq and @domSalReq)**/
			)
			) AND op.id_operario NOT IN (
			SELECT op.id_operario FROM dbo.detalle_lista_operarios3 op
			INNER JOIN Operarios_remplazosdet rem on rem.remplazo_id=op.id_operario 
			INNER JOIN Operarios_asignaciondet asd on rem.Asignacion_id=asd.id
			inner JOIN Operarios_asignacioncab ac on ac.id=asd.asignacionCab_id
			inner JOIN Operarios_puntoservicio ps on ps.id=ac.puntoServicio_id
			inner JOIN Operarios_relevamientocab rc on rc.puntoServicio_id=ps.id AND  rc.estado='Aprobado' 
			LEFT JOIN Operarios_dialibre dl on dl.id_operario_id=op.id_operario
			WHERE 
			(op.totalHoras+cast(isnull(@totalHoras,0)  as float)>@horasMaximas
			
			
			or((
				(@fechaFin>=asd.fechaInicio and (@fechaFin <=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23)>=asd.fechaInicio and (convert(date, @fechaInicioOperario)<=asd.fechaFin or asd.fechaFin is null))
				or (convert(date, @fechaInicioOperario, 23) <=asd.fechaInicio and (@fechaFin>=asd.fechaFin or asd.fechaFin is NULL))
				)
			AND(
				(asd.lunEnt between @lunEntReqTras and @lunSalReq) or (asd.lunSal  between @lunEntReqTras and @lunSalReq) 
				or (asd.marEnt between @marEntReqTras and @marSalReq) or (asd.marSal   between @marEntReqTras and @marSalReq)
				or (asd.mieEnt between @mierEntReqTras and @mierSalReq) or (asd.mieSal  between @mierEntReqTras and @mierSalReq)
				or (asd.jueEnt between @jueEntReqTras and @jueSalReq) or (asd.jueSal between @jueEntReqTras and  @jueSalReq)
				or (asd.vieEnt between @vieEntReqTras and @vieSalReq) or (asd.vieSal  between  @vieEntReqTras and @vieSalReq)
				or (asd.sabEnt between @sabEntReqTras and @sabSalReq) or (asd.sabSal  between @sabEntReqTras and @sabSalReq)
				or (asd.domEnt between @domEntReqTras and @domSalReq) or (asd.domSal  between @domEntReqTras and @domSalReq)
			
			))
			
			/**traemos los que tienen dia libre en ese dia del requerimiento**/
			/*or (dl.lunEnt between @lunEntReq and @lunSalReq) or (dl.lunSal between @lunEntReq and @lunSalReq)
			or (dl.marEnt between @marEntReq and @marSalReq) or (dl.marSal between @marEntReqTras and @marSalReq)
			or (dl.mieEnt between @mierEntReq and @mierSalReq) or (dl.mieSal  between @mierEntReq and @mierSalReq)
			or (dl.jueEnt between  @jueEntReq and @jueSalReq)
			or (dl.jueSal between  @jueEntReq and @jueSalReq)
			or (dl.vieEnt between  @vieEntReq and @vieSalReq)  
			or (dl.sabEnt between @sabEntReq and @sabSalReq) or (dl.sabSal  between @sabEntReq and @sabSalReq)
			or (dl.domEnt  between @domEntReq and @domSalReq) or (dl.domSal  between @domEntReq and @domSalReq)*/
			)
			)



		AND ((LEN(@perfil)>0 and op.ids_perfil like '%'+@perfil+'%') or LEN(@perfil)=0)
		ORDER BY op.totalHoras asc, op.nombres asc
	END
GO
/****** Object:  StoredProcedure [dbo].[ordenServicioCab_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE         PROCEDURE [dbo].[ordenServicioCab_trg]   
	@json nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		declare @fechaCambio datetime;
		set @fechaCambio=CURRENT_TIMESTAMP;
		DECLARE @TransactionName varchar(20) = 'Transactional';
		Declare @err_msg nvarchar(max);
		BEGIN TRAN @TransactionName 
		BEGIN TRY
			DECLARE @tmp1_vregistro int;
			DECLARE @delete nvarchar(max);
			DECLARE @p_cantHoras nvarchar(8);
			DECLARE @p_activo bit ;
			DECLARE @p_facturar bit;
			DECLARE @p_estado nvarchar(3);
			DECLARE @p_nroCotizacion nvarchar(30);

			--DECLARE @p_tipoHora_id int;
			DECLARE @p_tipoOrden_id int;
			DECLARE @p_numCantHoras int;
			DECLARE @p_cantidad int;
			DECLARE @p_usuario_id int;
			DECLARE @p_id int;
			DECLARE @p_puntoServicio_id int;
			declare @p_numHorasDobDiu int;
			declare @p_numHorasDobNoc int;
			declare @p_numHorasFerDiu int;
			declare @p_numHorasFerNoc int;
			declare @p_numHorasNorDiu int;
			declare @p_numHorasNorNoc int;

			DECLARE @p_fecha date ;
			DECLARE @p_fechaFin date ;


			select @p_activo="value" from OpenJson(@json) where "key"='activo' and "value"!='None';
			select @p_facturar="value" from OpenJson(@json) where "key"='facturar' and "value"!='None';
			select @p_estado="value" from OpenJson(@json) where "key"='estado' and "value"!='None';
			select @p_Fecha=convert(datetime,"value",103) from OpenJson(@json) where "key"='Fecha' and "value"!='None';
			select @p_fechaFin=convert(datetime,"value",103) from OpenJson(@json) where "key"='fechaFin' and "value"!='None';
			select @p_cantHoras="value" from OpenJson(@json) where "key"='cantHoras' and "value"!='None';
			select @p_numCantHoras=cast("value" as int) from OpenJson(@json) where "key"='numCantHoras' and "value"!='None';
			select @p_nroCotizacion="value" from OpenJson(@json) where "key"='nroCotizacion' and "value"!='None';
			select @p_puntoServicio_id=cast("value" as int) from OpenJson(@json) where "key"='puntoServicio_id' and "value"!='None';
			--select @p_tipoHora_id=cast("value" as int) from OpenJson(@json) where "key"='tipoHora_id' and "value"!='None';
			select @p_tipoOrden_id=cast("value" as int) from OpenJson(@json) where "key"='tipoOrden_id' and "value"!='None';
			select @p_usuario_id=cast("value" as int) from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
			select @p_id=cast("value" as int) from OpenJson(@json) where "key"='id' and "value"!='None';
			select @p_numHorasDobDiu=cast("value" as int) from OpenJson(@Json) where "key"='numHorasDobDiu' and "value"!='None';
			select @p_numHorasDobNoc=cast("value" as int) from OpenJson(@Json) where "key"='numHorasDobNoc' and "value"!='None';
			select @p_numHorasFerDiu=cast("value" as int) from OpenJson(@Json) where "key"='numHorasFerDiu' and "value"!='None';
			select @p_numHorasFerNoc=cast("value" as int) from OpenJson(@Json) where "key"='numHorasFerNoc' and "value"!='None';
			select @p_numHorasNorDiu=cast("value" as int) from OpenJson(@Json) where "key"='numHorasNorDiu' and "value"!='None';
			select @p_numHorasNorNoc=cast("value" as int) from OpenJson(@Json) where "key"='numHorasNorNoc' and "value"!='None';
			if @p_fecha is NULL
			begin
				SET @p_fecha=CURRENT_TIMESTAMP
			end


			if  @p_id is not NULL
			begin
				select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histordenServiciocab where vactual_id=@p_id;
				if @tmp1_vregistro is NULL
				begin
					set @tmp1_vregistro=1;
					INSERT INTO dbo.Operarios_histordenServiciocab(activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin,numeroOrden)
					select activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,@p_id,NULL,@fechaCambio,@tmp1_vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin,numeroOrden from dbo.Operarios_ordenServiciocab where id=@p_id;
				end
				update dbo.Operarios_histordenServiciocab set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro;
				set @tmp1_vregistro=@tmp1_vregistro+1;
				INSERT INTO dbo.Operarios_histordenServiciocab(activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin)
				select @p_activo,@p_facturar,@p_estado,@p_Fecha,@p_cantHoras,@p_numCantHoras,@p_nroCotizacion,@p_puntoServicio_id,@p_tipoOrden_id,@p_usuario_id,@p_id,NULL,@fechaCambio,@tmp1_vregistro,@p_numHorasDobDiu,@p_numHorasDobNoc,@p_numHorasFerDiu,@p_numHorasFerNoc,@p_numHorasNorDiu,@p_numHorasNorNoc,@p_fechaFin
				update dbo.Operarios_ordenServiciocab set 
					activo=@p_activo,
					facturar=@p_facturar,
					estado=@p_estado,
					Fecha=@p_Fecha,
					fechaFin=@p_fechaFin,
					cantHoras=@p_cantHoras,
					numCantHoras=@p_numCantHoras,
					nroCotizacion=@p_nroCotizacion,
					puntoServicio_id=@p_puntoServicio_id,
					tipoOrden_id=@p_tipoOrden_id,
					numHorasDobDiu=@p_numHorasDobDiu,
					numHorasDobNoc=@p_numHorasDobNoc,
					numHorasFerDiu=@p_numHorasFerDiu,
					numHorasFerNoc=@p_numHorasFerNoc,
					numHorasNorDiu=@p_numHorasNorDiu,
					numHorasNorNoc=@p_numHorasNorNoc,
					usuario_id=@p_usuario_id
					where id=@p_id;
			end
			if  @p_id is NULL
			begin
				set @tmp1_vregistro=1;
				declare @nxt int;
				declare @txt nvarchar(7);
				select @nxt=NEXT VALUE FOR numero_orden_servicio;
				select @txt=REPLACE(Str(@nxt,7),' ','0')

				INSERT INTO dbo.Operarios_ordenServiciocab(activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin,numeroOrden)
				select @p_activo,@p_facturar,@p_estado,@p_Fecha,@p_cantHoras,@p_numCantHoras,@p_nroCotizacion,@p_puntoServicio_id,@p_tipoOrden_id,@p_usuario_id,@p_numHorasDobDiu,@p_numHorasDobNoc,@p_numHorasFerDiu,@p_numHorasFerNoc,@p_numHorasNorDiu,@p_numHorasNorNoc,@p_fechaFin,@txt;
				set @p_id=SCOPE_IDENTITY();
				INSERT INTO dbo.Operarios_histordenServiciocab(activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin,numeroOrden)
				select @p_activo,@p_facturar,@p_estado,@p_Fecha,@p_cantHoras,@p_numCantHoras,@p_nroCotizacion,@p_puntoServicio_id,@p_tipoOrden_id,@p_usuario_id,@p_id,NULL,@fechaCambio,@tmp1_vregistro,@p_numHorasDobDiu,@p_numHorasDobNoc,@p_numHorasFerDiu,@p_numHorasFerNoc,@p_numHorasNorDiu,@p_numHorasNorNoc,@p_fechaFin,@txt
			end
				COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		SET @retorno=1;
		ROLLBACK TRAN @TransactionName; 
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json);
		Select 1 as resultado;
		RETURN 1;
	END CATCH
	Select 0 as resultado;
	RETURN 0;
END
GO
/****** Object:  StoredProcedure [dbo].[OrdServ_det_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE         PROCEDURE [dbo].[OrdServ_det_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_horaInicio  time;
		DECLARE @p_horaFin  time;
		DECLARE @p_fecha  date;
		DECLARE @p_activo  bit;
		DECLARE @p_pagoDoble  bit;
		DECLARE @p_observacion  nvarchar(200);
		DECLARE @p_operario_id  int;
		DECLARE @p_ordenServicioCab_id  int;
		DECLARE @p_usuario_id int;
		DECLARE @p_id int;
		
		select @p_horaInicio="value" from OpenJson(@json) where "key" ='horaInicio' and value!='None';
		select @p_horaFin="value" from OpenJson(@json) where "key" ='horaFin' and value!='None';
		select @p_fecha=convert(datetime,"value",103) from OpenJson(@json) where "key" ='fecha' and value!='None';
		select @p_activo="value" from OpenJson(@json) where "key" ='activo' and value!='None';
		select @p_pagoDoble=case when "value" is NULL then 'False' else "value" end from OpenJson(@json) where "key" ='pagoDoble' and value!='None';
		select @p_observacion="value" from OpenJson(@json) where "key" ='observacion' and value!='None';
		select @p_operario_id=cast("value" as int) from OpenJson(@json) where "key" ='operario_id' and value!='None';
		select @p_ordenServicioCab_id=cast("value" as int) from OpenJson(@json) where "key" ='ordenServicioCab_id' and value!='None';
		select @p_usuario_id=cast("value" as int) from OpenJson(@json) where "key" ='usuario_id' and value!='None';
		select @p_id=cast("value" as int) from OpenJson(@json) where "key"='id' and "value"!='None';
		
		
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histordenServiciocab where vactual_id=@p_ordenServicioCab_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histordenServicioDet(horaInicio,horaFin,fecha,activo,observacion,operario_id,ordenServicioCab_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,pagoDoble)
				select horaInicio,horaFin,fecha,activo,observacion,operario_id,ordenServicioCab_id,usuario_id,@p_id,NULL,@fechaCambio,@tmp1_vregistro,@p_pagoDoble from dbo.Operarios_ordenServicioDet where id=@p_id;
			end
			INSERT INTO dbo.Operarios_histordenServiciocab(activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin)
			select activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,@p_ordenServicioCab_id,NULL,@fechaCambio,@tmp1_vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin from dbo.Operarios_ordenServiciocab where id=@p_ordenServicioCab_id;
			update dbo.Operarios_histordenServicioDet set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			--if @delete is not NULL and @delete='False'
			--begin
			INSERT INTO dbo.Operarios_histordenServicioDet(horaInicio,horaFin,fecha,activo,observacion,operario_id,ordenServicioCab_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,pagoDoble)
			select @p_horaInicio,@p_horaFin,@p_fecha,@p_activo,@p_observacion,@p_operario_id,@p_ordenServicioCab_id,@p_usuario_id,@p_id,NULL,@fechaCambio,@tmp1_vregistro,@p_pagoDoble
			update dbo.Operarios_ordenServicioDet set 
					horaInicio=@p_horaInicio,
					horaFin=@p_horaFin,
					fecha=@p_fecha,
					activo=@p_activo,
					pagoDoble=@p_pagoDoble,
					observacion=@p_observacion,
					operario_id=@p_operario_id,
					ordenServicioCab_id=@p_ordenServicioCab_id,
					usuario_id=@p_usuario_id
					where id=@p_id;
			--end
			/*if @delete is not NULL and @delete='True'
			begin
				update Operarios_histordenServicioDet set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_ordenServicioDet  where id=@p_id;
			end*/
		end
		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histordenServiciocab where vactual_id=@p_ordenServicioCab_id;
			INSERT INTO dbo.Operarios_ordenServicioDet(horaInicio,horaFin,fecha,activo,observacion,operario_id,ordenServicioCab_id,usuario_id,pagoDoble)
			select @p_horaInicio,@p_horaFin,@p_fecha,@p_activo,@p_observacion,@p_operario_id,@p_ordenServicioCab_id,@p_usuario_id,@p_pagoDoble
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histordenServicioDet(horaInicio,horaFin,fecha,activo,observacion,operario_id,ordenServicioCab_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,pagoDoble)
			select @p_horaInicio,@p_horaFin,@p_fecha,@p_activo,@p_observacion,@p_operario_id,@p_ordenServicioCab_id,@p_usuario_id,@p_id,NULL,@fechaCambio,@tmp1_vregistro,@p_pagoDoble
		end
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[oS_estado_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create   PROCEDURE [dbo].[oS_estado_trg]   
	@p_id int,
	@p_estado nvarchar(3),
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		declare @fechaCambio datetime;
		set @fechaCambio=CURRENT_TIMESTAMP;
		DECLARE @TransactionName varchar(20) = 'Transactional';
		Declare @err_msg nvarchar(max);
		BEGIN TRAN @TransactionName 
		BEGIN TRY
			DECLARE @tmp1_vregistro int;
			DECLARE @delete nvarchar(max);
			if  @p_id is not NULL
			begin
				select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histordenServiciocab where vactual_id=@p_id;
				if @tmp1_vregistro is NULL
				begin
					set @tmp1_vregistro=1;
					INSERT INTO dbo.Operarios_histordenServiciocab(activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin)
					select activo,facturar,@p_estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,id,NULL,@fechaCambio,@tmp1_vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin from dbo.Operarios_ordenServiciocab where id=@p_id;
				end
				update dbo.Operarios_histordenServiciocab set vfechaFin=@fechaCambio where vactual_id=id and vregistro=@tmp1_vregistro;
				set @tmp1_vregistro=@tmp1_vregistro+1;
				INSERT INTO dbo.Operarios_histordenServiciocab(activo,facturar,estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,vactual_id,vfechaFin,vfechaInicio,vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin)
				select activo,facturar,@p_estado,Fecha,cantHoras,numCantHoras,nroCotizacion,puntoServicio_id,tipoOrden_id,usuario_id,id,NULL,@fechaCambio,@tmp1_vregistro,numHorasDobDiu,numHorasDobNoc,numHorasFerDiu,numHorasFerNoc,numHorasNorDiu,numHorasNorNoc,fechaFin from dbo.Operarios_ordenServiciocab where id=@p_id;
				update dbo.Operarios_ordenServiciocab set 
					estado=@p_estado
					where id=@p_id;
			end
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		SET @retorno=1;
		ROLLBACK TRAN @TransactionName; 
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		Select 1 as resultado;
		RETURN 1;
	END CATCH
	Select 0 as resultado;
	RETURN 0;
END
GO
/****** Object:  StoredProcedure [dbo].[os_listar_detalles]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE      PROCEDURE [dbo].[os_listar_detalles]   
	@oscab int,
	@retorno int OUTPUT
AS   
    BEGIN
		set nocount on;
		DECLARE @horasMaximas int =0;
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
		DECLARE @fechaFin date;
		DECLARE @fechaInicio date;
		SElect @fechaFin= max(fecha) from dbo.Operarios_ordenserviciodet where ordenServicioCab_id=@oscab;
		SElect @fechaInicio= max(fecha) from dbo.Operarios_ordenserviciodet where ordenServicioCab_id=@oscab;
		SELECT @horasMaximas=cast(valor as int) FROM dbo.Operarios_parametros WHERE tipo='BUSQUEDA' AND parametro='MAXIMO_ASIGNACION'
	
		CREATE table #semanas (
			inicio datetime,
			fin datetime,
			dias int,
			semana int
		);
		declare @fi datetime;
		insert into #semanas EXEC[dbo].[partirSemanas]
		@fechaInicio = @fechaInicio,
		@fechaFin = @fechaFin;

	SELECT 
	   [osdetout].[id]
      ,[osdetout].[horaInicio]
      ,[osdetout].[horaFin]
      ,[osdetout].[fecha]
      ,[osdetout].[activo]
      ,[osdetout].[observacion]
      ,[osdetout].[operario_id]
      ,[osdetout].[ordenServicioCab_id]
      ,[osdetout].[usuario_id]
	  ,[osdetout].[pagoDoble]
	  , (select case when @horasMaximas>sum(resum.totalHoras) then 'False' else 'True' end as supera from (SELECT        op.id AS id_operario, op.ciudad_id AS ciudad, { fn CONCAT({ fn CONCAT(op.nombre, ' ') }, op.apellido) } AS nombres, op.nroLegajo,/* ISNULL(STRING_AGG(ps.NombrePServicio, ', '), '') AS nombres_puntoServicio, */
                                                    /*ISNULL(STRING_AGG(ps.id, ', '), ' ') AS ids_puntoServicio, */
													SUM(CAST(ISNULL(aod.numTotalHoras, 0) AS float)) + 
													SUM(CAST(ISNULL(aodt.numTotalHoras, 0) AS float))+
													SUM(CAST(ISNULL(asdet.numTotalHoras, 0) AS float))+
													SUM(CAST(ISNULL(DATEDIFF(MI,osdet.horaInicio,osdet.horaFin),0) as float))
													AS totalHoras, 
													aod.fechaInicio as fi1,
													aod.fechaFin as ff1,
													osdet.fecha as fi2,
													rempdet.fecha as fi3,
													rempdet.fechaFin as ff3,
													aodt.fechaInicio as fi4,
													aodt.fechaFin as ff4,
													DATEDIFF(year, op.fechaInicio, GETDATE()) AS antiguedad,
													ss.inicio,
													ss.fin,
													ss.dias,
													ss.semana
                          FROM            dbo.Operarios_operario AS op LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondet aod ON op.id = aod.operario_id LEFT OUTER JOIN
													dbo.Operarios_ordenserviciodet osdet on osdet.operario_id=op.id left outer join
													dbo.Operarios_remplazosdet rempdet on rempdet.remplazo_id=op.id left outer join
													dbo.Operarios_asignaciondet  asdet ON rempdet.Asignacion_id=asdet.id LEFT OUTER JOIN
                                                    dbo.Operarios_asignaciondettemp  aodt ON op.id = aodt.operario_id LEFT OUTER JOIN
                                                    dbo.Operarios_ciudad AS cd ON cd.id = op.ciudad_id
													right outer join #semanas ss on
													 (
													 
													 (ss.semana>= datepart(WW,aod.fechaInicio) and
													 ss.semana<= datepart(WW,aod.fechaFin))

													 or(ss.semana>= datepart(WW,rempdet.fecha) and
													 ss.semana<= datepart(WW,rempdet.fechaFin))

													 OR(ss.semana= datepart(WW,osdet.fecha) )
													 
													 OR(ss.semana>= datepart(WW,aodt.fechaInicio) and
													 ss.semana<= datepart(WW,aodt.fechaFin))
													 
													 )

                          GROUP BY op.id, op.nombre, op.apellido, op.nroLegajo, op.fechaInicio, op.ciudad_id,aod.fechaInicio,aod.fechaFin,osdet.fecha,rempdet.fecha,rempdet.fechaFin,aodt.fechaInicio,
						  aodt.fechaFin,ss.inicio,ss.fin,ss.dias,ss.semana 
						  having op.id=osdetout.operario_id) resum) as supera
	 FROM [dbo].[Operarios_ordenserviciodet] osdetout
	 where osdetout.ordenServicioCab_id=@oscab and osdetout.activo='True'
	END
GO
/****** Object:  StoredProcedure [dbo].[oServicio_datelle_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

create          PROCEDURE [dbo].[oServicio_datelle_manager]   
	@json_ope nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
			DECLARE @RC int;
			DECLARE @tmp nvarchar(max);
			/*det*/
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_ope)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[OrdServ_det_trg] @tmp,@fechaCambio,@retorno
				end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_ope);
	END CATCH
	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[partirDias]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE          PROCEDURE [dbo].[partirDias]    
	@fechaInicio datetime,
	@fechaFin datetime
AS   
    BEGIN
		LINENO 0;
		SET DATEFIRST 1;
		with alldays as (
			select @fechaInicio as 'fecha'
				union all 
			select DATEADD(DAY,1,al.fecha) from alldays al where al.fecha<@fechaFin) 
		select al2.fecha as 'fecha',DATEPART(DW,al2.fecha) as 'dia' from alldays al2 option(MAXRECURSION 32767) 
	END
GO
/****** Object:  StoredProcedure [dbo].[partirMeses]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create          PROCEDURE [dbo].[partirMeses]    
	@fechaInicio datetime,
	@fechaFin datetime
AS   
    BEGIN
		LINENO 0;
		SET DATEFIRST 1;
		with alldays as (
			select @fechaInicio as 'fecha',datepart(MM,@fechaInicio) as 'mes', 1 as 'nivel'
				union all 
			select DATEADD(DAY,1,al.fecha),datepart(MM, DATEADD(DAY,1,al.fecha)),al.nivel from alldays al where al.fecha<@fechaFin) 
		select min(al2.fecha) as 'inicio',max(al2.fecha) as 'fin ', Datediff(DAY,min(al2.fecha),max(al2.fecha)) as 'dias',al2.mes from alldays al2 group by al2.mes option(MAXRECURSION 32767) 
	END
GO
/****** Object:  StoredProcedure [dbo].[partirMesesXN]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE    PROCEDURE [dbo].[partirMesesXN]    
	@fechaInicio datetime,
	@fechaFin datetime,
	@partir int
AS   
    BEGIN
		LINENO 0;
		declare @diallegar int;
		Set @diallegar=datepart(DD,@fechaInicio)-1;
		SET DATEFIRST 1;
		with alldays as (
			select @fechaInicio as 'fecha',datepart(MM,@fechaInicio) as 'mes',datepart(YYYY,@fechaInicio) as 'anho', 1 as 'nivel'
				union all 
			select DATEADD(DAY,1,al.fecha),datepart(MM, DATEADD(DAY,1,al.fecha)),datepart(YYYY, DATEADD(DAY,1,al.fecha)),al.nivel from alldays al where al.fecha<@fechaFin) 
		select min(al2.fecha)  as 'inicio',max(al2.fecha) as 'fin ', Datediff(DAY,min(al2.fecha),max(al2.fecha)) as 'dias',al2.mes,al2.anho from alldays al2 group by al2.anho,al2.mes  having (((al2.anho-datepart(YYYY,(select top(1) fecha from alldays order by fecha asc) ))*12)+al2.mes-datepart(MM,(select top(1) fecha from alldays order by fecha asc)))%@partir=0 and max(al2.fecha)<=@fechaFin order by al2.anho asc,al2.mes asc  option(MAXRECURSION 32767) 
	
	 
	END
GO
/****** Object:  StoredProcedure [dbo].[partirSemanas]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE        PROCEDURE [dbo].[partirSemanas]    
	@fechaInicio datetime,
	@fechaFin datetime
AS   
    BEGIN
		LINENO 0;
		SET DATEFIRST 1;
		with alldays as (
			select @fechaInicio as 'fecha',datepart(WW,@fechaInicio) as 'semana', 1 as 'nivel'
				union all 
			select DATEADD(DAY,1,al.fecha),datepart(WW, DATEADD(DAY,1,al.fecha)),al.nivel from alldays al where al.fecha<@fechaFin) 
		select min(al2.fecha) as 'inicio',max(al2.fecha) as 'fin ', Datediff(DAY,min(al2.fecha),max(al2.fecha)) as 'dias',al2.semana from alldays al2 group by al2.semana option(MAXRECURSION 32767) 
	END
GO
/****** Object:  StoredProcedure [dbo].[planificacion_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE        PROCEDURE [dbo].[planificacion_manager]   
	@json_cab nvarchar(max),
	@json_ope nvarchar(max),
	--@json_esp nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
			DECLARE @RC int;
			DECLARE @tmp nvarchar(max);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_ope);
			--insert into infolog(fechaHora,info) values(@fechaCambio,@json_esp);

			EXECUTE @RC = [dbo].[planificacioncab_trg] @json_cab,@fechaCambio,@retorno
			/*det*/
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_ope)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[planificacionope_trg] @tmp,@fechaCambio,@retorno
				end



			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt
			/*ESP
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_esp)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[planificacionesp_trg] @tmp,@fechaCambio,@retorno
				end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt*/
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_ope);
		--insert into infolog(fechaHora,info) values(@fechaCambio,@json_esp);
	END CATCH
	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[planificacion_unica_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE   PROCEDURE [dbo].[planificacion_unica_manager]   
	@json_cab nvarchar(max),
	--@json_ope nvarchar(max),
	@json_esp nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
			DECLARE @RC int;
			DECLARE @tmp nvarchar(max);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
			--insert into infolog(fechaHora,info) values(@fechaCambio,@json_ope);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_esp);

			EXECUTE @RC = [dbo].[planificacioncab_trg] @json_cab,@fechaCambio,@retorno
			/*det
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_ope)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[planificacionope_trg] @tmp,@fechaCambio,@retorno
				end



			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt*/
			/*ESP*/
			/*DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_esp)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin*/
					EXECUTE @RC = [dbo].[planificacionesp_trg] @json_esp,@fechaCambio,@retorno
				/*end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt*/
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
		--insert into infolog(fechaHora,info) values(@fechaCambio,@json_ope);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_esp);
	END CATCH
	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[planificacioncab_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[planificacioncab_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_puntoServicio_id int;
		DECLARE @p_cantHorasEsp nvarchar(8);
		DECLARE @p_cantHorasNoc nvarchar(8);
		DECLARE @p_cantHoras nvarchar(8);
		DECLARE @p_numCantHorasEsp int;
		DECLARE @p_numCantHorasNoc int;
		DECLARE @p_numCantHoras int;
		DECLARE @p_cantidad int;
		DECLARE @p_usuario_id int;
		DECLARE @p_fecha datetime2 ;
		DECLARE @p_id int;

		select @p_puntoServicio_id="value" from OpenJson(@json) where "key"='puntoServicio_id' and "value"!='None';
		select @p_cantHorasEsp="value" from OpenJson(@json) where "key"='cantHorasEsp' and "value"!='None';
		select @p_cantHorasNoc="value" from OpenJson(@json) where "key"='cantHorasNoc' and "value"!='None';
		select @p_cantHoras="value" from OpenJson(@json) where "key"='cantHoras' and "value"!='None';
		select @p_numCantHorasEsp="value" from OpenJson(@json) where "key"='numCantHorasEsp' and "value"!='None';
		select @p_numCantHorasNoc="value" from OpenJson(@json) where "key"='numCantHorasNoc' and "value"!='None';
		select @p_numCantHoras="value" from OpenJson(@json) where "key"='numCantHoras' and "value"!='None';
		select @p_usuario_id="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
		select @p_cantidad="value" from OpenJson(@json) where "key"='cantidad'  and "value"!='None';
		select @p_fecha="value" from OpenJson(@json) where "key"='fecha' and "value"!='None';
		select @p_id="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if @p_fecha is NULL
		begin
			SET @p_fecha=CURRENT_TIMESTAMP
		end


		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histplanificacioncab where vactual_id=@p_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histplanificacioncab(puntoServicio_id,cantHorasEsp,cantHorasNoc,cantHoras,cantidad,fecha,vfechaInicio,vfechaFin,vregistro,vactual_id,rePlanificar,usuario_id,numCantHoras,numCantHorasNoc,numCantHorasEsp)
				select puntoServicio_id,cantHorasEsp,cantHorasNoc,cantHoras,cantidad,fecha,@fechaCambio,NULL,@tmp1_vregistro,@p_id,rePlanificar,usuario_id,numCantHoras,numCantHorasNoc,numCantHorasEsp from dbo.Operarios_planificacioncab where id=@p_id;
			end
			update dbo.Operarios_histplanificacioncab set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro;
			set @tmp1_vregistro=@tmp1_vregistro+1;
			INSERT INTO dbo.Operarios_histplanificacioncab(puntoServicio_id,cantHorasEsp,cantHorasNoc,cantHoras,cantidad,fecha,vfechaInicio,vfechaFin,vregistro,vactual_id,rePlanificar,usuario_id,numCantHoras,numCantHorasNoc,numCantHorasEsp)
			select @p_puntoServicio_id,@p_cantHorasEsp,@p_cantHorasNoc,@p_cantHoras,@p_cantidad,@p_fecha,@fechaCambio,NULL,@tmp1_vregistro,@p_id,'False',@p_usuario_id,@p_numCantHoras,@p_numCantHorasNoc,@p_numCantHorasEsp
			update dbo.Operarios_planificacioncab set 
				 puntoServicio_id=@p_puntoServicio_id,cantHorasEsp=@p_cantHorasEsp,
				 cantHorasNoc=@p_cantHorasNoc,cantHoras=@p_cantHoras,cantidad=@p_cantidad,fecha=@p_fecha, 
				 rePlanificar='False',usuario_id=@p_usuario_id,numCantHoras=@p_numCantHoras,numCantHorasNoc=@p_numCantHorasNoc,numCantHorasEsp=@p_numCantHorasEsp where id=@p_id;
		end
		if  @p_id is NULL
		begin
			set @tmp1_vregistro=1;
			INSERT INTO dbo.Operarios_planificacioncab(puntoServicio_id,cantHorasEsp,cantHorasNoc,cantHoras,cantidad,fecha,rePlanificar,usuario_id,numCantHoras,numCantHorasNoc,numCantHorasEsp)
			select @p_puntoServicio_id,@p_cantHorasEsp,@p_cantHorasNoc,@p_cantHoras,@p_cantidad,@p_fecha,'False',@p_usuario_id,@p_numCantHoras,@p_numCantHorasNoc,@p_numCantHorasEsp;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histplanificacioncab(puntoServicio_id,cantHorasEsp,cantHorasNoc,cantHoras,cantidad,fecha,vfechaInicio,vfechaFin,vregistro,vactual_id,rePlanificar,usuario_id,numCantHoras,numCantHorasNoc,numCantHorasEsp)
			select @p_puntoServicio_id,@p_cantHorasEsp,@p_cantHorasNoc,@p_cantHoras,@p_cantidad,@p_fecha,@fechaCambio,NULL,@tmp1_vregistro,@p_id,'False',@p_usuario_id,@p_numCantHoras,@p_numCantHorasNoc,@p_numCantHorasEsp
		end
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[planificacionesp_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[planificacionesp_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_fechaLimpProf date;
		DECLARE @p_cantHoras nvarchar(8);
		DECLARE @p_estado nvarchar(3);
		DECLARE @p_numCantHoras int;
		DECLARE @p_tipo_id int;
		declare @sector nvarchar(max);
		declare @area nvarchar(50);
		declare @cantidad int;
		DECLARE @p_planificacionCab_id int;
		DECLARE @p_especialista_id int;
		DECLARE @p_especialista int;
		DECLARE @p_tipo int;
		DECLARE @p_tipoHora_id int;
		DECLARE @p_frecuencia nvarchar(3) ;
		DECLARE @p_id int;
		DECLARE @p_id_gn int;
		declare @gen_new bit = 'False';
		--select @json
		select @p_fechaLimpProf=convert(date,"value",23) from OpenJson(@json) where "key"='fechaLimpProf' and "value"!='None';
		select @p_cantHoras="value" from OpenJson(@json) where "key"='cantHoras' and "value"!='None' ;
		select @sector="value" from OpenJson(@json) where "key"='sector';
		select @area="value" from OpenJson(@json) where "key"='area';
		select @cantidad=cast("value" as int) from OpenJson(@json) where "key"='cantidad' and "value"!='None';
		select @p_numCantHoras="value" from OpenJson(@json) where "key"='numCantHoras' and "value"!='None' ;
		select @p_tipo_id="value" from OpenJson(@json) where "key"='tipo' and "value"!='None' ;
		select @p_tipoHora_id="value" from OpenJson(@json) where "key"='tipoHora_id' and "value"!='None' ;
		select @delete="value" from OpenJson(@json) where "key"='DELETE' and "value"!='None' ;
		select @p_planificacionCab_id="value" from OpenJson(@json) where "key"='planificacionCab_id' and "value"!='None' ;
		select @p_especialista_id="value" from OpenJson(@json) where "key"='especialista' and "value"!='None' ;
		select @p_frecuencia="value" from OpenJson(@json) where "key"='frecuencia' and "value"!='None' ;
		select @p_estado="value" from OpenJson(@json) where "key"='estado' and "value"!='None' ;
		insert into dbo.infolog(info,fechaHora)values('estado',CURRENT_TIMESTAMP);
		insert into dbo.infolog(info,fechaHora)values(@p_estado,CURRENT_TIMESTAMP);
		if @p_estado is NULL
		begin
			set @p_estado='PVC'
		end
		if @p_estado ='FIN'
		begin
			set @gen_new='True'
		end
		select @p_id=cast("value" as int)  from OpenJson(@json) where "key"='id' and "value"!='None';
		insert into dbo.infolog(info,fechaHora)values(@p_id,CURRENT_TIMESTAMP);
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histplanificacioncab where vactual_id=@p_planificacionCab_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				insert into dbo.infolog(info,fechaHora)values('camino NO esperado 1',CURRENT_TIMESTAMP);
				INSERT INTO dbo.Operarios_histplanificacionesp(fechaLimpProf,cantHoras,tipo_id,planificacionCab_id,especialista_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,estado,sector,area,cantidad,tipoHora_id)
				select fechaLimpProf,cantHoras,tipo_id,planificacionCab_id,especialista_id,frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_estado,@sector,@area,@cantidad,@p_tipoHora_id from dbo.Operarios_planificacionesp where id=@p_id;
			end
			insert into dbo.infolog(info,fechaHora)values('camino esperado 1',CURRENT_TIMESTAMP);
			update dbo.Operarios_histplanificacionesp set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				if @gen_new = 'True'
				begin
					INSERT INTO dbo.Operarios_planificacionesp(fechaLimpProf,cantHoras,tipo_id,planificacionCab_id,especialista_id,frecuencia,numCantHoras,estado,sector,area,cantidad,tipoHora_id)
					select dateadd(YEAR,1,@p_fechaLimpProf),@p_cantHoras,@p_tipo_id,@p_planificacionCab_id,@p_especialista_id,@p_frecuencia,@p_numCantHoras,@p_estado,@sector,@area,@cantidad,@p_tipoHora_id;
					set @p_id_gn=SCOPE_IDENTITY();
					insert into dbo.infolog(info,fechaHora)values('camino no esperado 2',CURRENT_TIMESTAMP);
					INSERT INTO dbo.Operarios_histplanificacionesp(fechaLimpProf,cantHoras,tipo_id,planificacionCab_id,especialista_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,estado,sector,area,cantidad,tipoHora_id)
					select fechaLimpProf,cantHoras,tipo_id,planificacionCab_id,especialista_id,frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_estado,@sector,@area,@cantidad,@p_tipoHora_id from dbo.Operarios_planificacionesp where id=@p_id_gn;
				end
				INSERT INTO dbo.Operarios_histplanificacionesp(fechaLimpProf,cantHoras,tipo_id,planificacionCab_id,especialista_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,estado,sector,area,cantidad,tipoHora_id)
				select @p_fechaLimpProf,@p_cantHoras,@p_tipo_id,@p_planificacionCab_id,@p_especialista_id,@p_frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_estado,@sector,@area,@cantidad,@p_tipoHora_id

				update dbo.Operarios_planificacionesp set 
					 fechaLimpProf=@p_fechaLimpProf,
					 cantHoras=@p_cantHoras,
					 tipoHora_id=@p_tipoHora_id,
					 sector=@sector,
					 area=@area,
					 estado=@p_estado ,
					 cantidad=@cantidad,
					 tipo_id=@p_tipo_id,
					 planificacionCab_id=@p_planificacionCab_id,
					 especialista_id=@p_especialista_id,
					 frecuencia=@p_frecuencia,
					 numCantHoras=@p_numCantHoras
					 where id=@p_id;
				insert into dbo.infolog(info,fechaHora)values('camino esperado final',CURRENT_TIMESTAMP);
			end

			if @delete is not NULL and @delete='True'
			begin
				insert into dbo.infolog(info,fechaHora)values('camino no esperado 3',CURRENT_TIMESTAMP);
				update Operarios_histplanificacionesp set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_planificacionesp  where id=@p_id;
			end
			

		end
		if  @p_id is NULL
		begin
			insert into dbo.infolog(info,fechaHora)values('camino no esperado 4',CURRENT_TIMESTAMP);
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histplanificacioncab where vactual_id=@p_planificacionCab_id;
			INSERT INTO dbo.Operarios_planificacionesp(fechaLimpProf,cantHoras,tipo_id,planificacionCab_id,especialista_id,frecuencia,numCantHoras,estado,sector,area,cantidad,tipoHora_id)
			select @p_fechaLimpProf,@p_cantHoras,@p_tipo_id,@p_planificacionCab_id,@p_especialista_id,@p_frecuencia,@p_numCantHoras,@p_estado,@sector,@area,@cantidad,@p_tipoHora_id;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histplanificacionesp(fechaLimpProf,cantHoras,tipo_id,planificacionCab_id,especialista_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,estado,sector,area,cantidad,tipoHora_id)
			select @p_fechaLimpProf,@p_cantHoras,@p_tipo_id,@p_planificacionCab_id,@p_especialista_id,@p_frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_estado,@sector,@area,@cantidad,@p_tipoHora_id
		end
		SET @retorno=0;
		--Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[planificacionope_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[planificacionope_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_total nvarchar(max);
		DECLARE @p_numTotal int;
		DECLARE @p_corte nvarchar(max);
		DECLARE @p_planificacionCab_id int;
		DECLARE @p_especialista_id int;
		DECLARE @p_sal time;
		DECLARE @p_ent time;
		DECLARE @p_fer bit ;
		DECLARE @p_dom bit ;
		DECLARE @p_sab bit ;
		DECLARE @p_vie bit ;
		DECLARE @p_jue bit ;
		DECLARE @p_mie bit ;
		DECLARE @p_mar bit ;
		DECLARE @p_lun bit ;
		DECLARE @p_cantidad int;
		DECLARE @p_id int;
		Declare @p_especialista nvarchar(max);
		

		select @p_total="value" from OpenJson(@json) where "key"='total';
		select @p_numTotal="value" from OpenJson(@json) where "key"='numTotal';
		select @p_corte="value" from OpenJson(@json) where "key"='corte';
		select @p_planificacionCab_id="value" from OpenJson(@json) where "key"='planificacionCab_id';
		select @p_especialista_id="value" from OpenJson(@json) where "key"='especialista_id';
		select @p_especialista="value" from OpenJson(@json) where "key"='especialista';
		select @p_sal="value" from OpenJson(@json) where "key"='sal' and "value"!='None';
		select @p_ent="value" from OpenJson(@json) where "key"='ent' and "value"!='None';
		select @p_fer="value" from OpenJson(@json) where "key"='fer';
		select @p_dom="value" from OpenJson(@json) where "key"='dom';
		select @p_sab="value" from OpenJson(@json) where "key"='sab';
		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @p_vie="value" from OpenJson(@json) where "key"='vie';
		select @p_jue="value" from OpenJson(@json) where "key"='jue';
		select @p_mie="value" from OpenJson(@json) where "key"='mie';
		select @p_mar="value" from OpenJson(@json) where "key"='mar';
		select @p_lun="value" from OpenJson(@json) where "key"='lun';
		select @p_cantidad="value" from OpenJson(@json) where "key"='cantidad';
		select @p_id="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		
		sELECT @p_especialista_id=id from dbo.Operarios_especializacion where especializacion like @p_especialista
		if  @p_especialista_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe especialidad');
		END
		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histplanificacioncab where vactual_id=@p_planificacionCab_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histplanificacionope(total,corte,planificacionCab_id,especialista_id,sal,ent,fer,dom,sab,vie,jue,mie,mar,lun,cantidad,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotal)
				select total,corte,planificacionCab_id,especialista_id,sal,ent,fer,dom,sab,vie,jue,mie,mar,lun,cantidad,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotal from dbo.Operarios_planificacionope where id=@p_id;
			end
			update dbo.Operarios_histplanificacionope set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				INSERT INTO dbo.Operarios_histplanificacionope(total,corte,planificacionCab_id,especialista_id,sal,ent,fer,dom,sab,vie,jue,mie,mar,lun,cantidad,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotal)
				select @p_total,@p_corte,@p_planificacionCab_id,@p_especialista_id,@p_sal,@p_ent,@p_fer,@p_dom,@p_sab,@p_vie,@p_jue,@p_mie,@p_mar,@p_lun,@p_cantidad,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotal
				update dbo.Operarios_planificacionope set 
					 total=@p_total,corte=@p_corte,planificacionCab_id=@p_planificacionCab_id,especialista_id=@p_especialista_id,sal=@p_sal,ent=@p_ent,fer=@p_fer,dom=@p_dom,sab=@p_sab,vie=@p_vie,jue=@p_jue,mie=@p_mie,mar=@p_mar,lun=@p_lun,cantidad=@p_cantidad,numTotal=@p_numTotal where id=@p_id;
			end
			if @delete is not NULL and @delete='True'
			begin
        update Operarios_histplanificacionope set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_planificacionope  where id=@p_id;
			end
		end
		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histplanificacioncab where vactual_id=@p_planificacionCab_id;
			INSERT INTO dbo.Operarios_planificacionope(total,corte,planificacionCab_id,especialista_id,sal,ent,fer,dom,sab,vie,jue,mie,mar,lun,cantidad,numTotal)
			select @p_total,@p_corte,@p_planificacionCab_id,@p_especialista_id,@p_sal,@p_ent,@p_fer,@p_dom,@p_sab,@p_vie,@p_jue,@p_mie,@p_mar,@p_lun,@p_cantidad,@p_numTotal;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histplanificacionope(total,corte,planificacionCab_id,especialista_id,sal,ent,fer,dom,sab,vie,jue,mie,mar,lun,cantidad,vfechaInicio,vfechaFin,vregistro,vactual_id,numTotal)
			select @p_total,@p_corte,@p_planificacionCab_id,@p_especialista_id,@p_sal,@p_ent,@p_fer,@p_dom,@p_sab,@p_vie,@p_jue,@p_mie,@p_mar,@p_lun,@p_cantidad,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numTotal
		end
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[puntoServicio_trigger]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[puntoServicio_trigger]   
  

	@p_id int,
	@p_CodPuntoServicio nvarchar(max),
	@p_NombrePServicio nvarchar(max),
	@p_DireccionContrato nvarchar(max),
	@p_Barrios nvarchar(max),
	@p_Contacto nvarchar(max),
	@p_MailContacto nvarchar(max),
	@p_TelefonoContacto nvarchar(max),
	@p_Coordenadas nvarchar(max),
	@p_Ciudad_id int,
	@p_Cliente_id int,
	@p_NumeroMarcador nvarchar(max),
	@p_usuario int,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	BEGIN TRAN @TransactionName 
	BEGIN TRY
	
		DECLARE @tmp1_vregistro int;
		DECLARE @nuevoID int;
		DECLARE @p_vfecha_inicio datetime;
		DECLARE @p_vfecha_fin datetime;
		DECLARE @p_vregistro int;
		Declare @fechaCambio datetime;

		SET @fechaCambio=CURRENT_TIMESTAMP;
	
		
		



		/* 1 - Punto de Servicio*/
				
				select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histpuntoservicio where vactual_id=@p_id;
				if @tmp1_vregistro is NULL
				begin
					set @tmp1_vregistro=1;
					INSERT INTO [dbo].[Operarios_histpuntoservicio]
					   ([CodPuntoServicio],[NombrePServicio],[DireccionContrato]
					   ,[Barrios],[Contacto],[MailContacto]
					   ,[TelefonoContacto],[Coordenadas],[NumeroMarcador]
					   ,[vfechaInicio],[vfechaFin],[vregistro]
					   ,[Ciudad_id],[Cliente_id],[vactual_id],activo,comentario,usuario_id)
					SELECT 
						[CodPuntoServicio],[NombrePServicio],[DireccionContrato],
						[Barrios],[Contacto],[MailContacto],
						[TelefonoContacto],[Coordenadas],[NumeroMarcador],
						@fechaCambio,NULL,1,
						[Ciudad_id],[Cliente_id],@p_id,activo,comentario,usuario_id
						from dbo.Operarios_puntoservicio where id=@p_id;
				end

				update dbo.Operarios_histpuntoservicio set vfechaFin=@fechaCambio where vactual_id=@p_id;

				update dbo.Operarios_puntoservicio set
					CodPuntoServicio=@p_CodPuntoServicio,
					NombrePServicio=@p_NombrePServicio,
					DireccionContrato=@p_DireccionContrato,
					Barrios=@p_Barrios,
					Contacto=@p_Contacto,
					MailContacto=@p_MailContacto,
					TelefonoContacto=@p_TelefonoContacto,
					Coordenadas=@p_Coordenadas,
					Ciudad_id=@p_Ciudad_id,
					Cliente_id=@p_Cliente_id,
					NumeroMarcador=@p_NumeroMarcador
					,usuario_id=@p_usuario
					where id=@p_id;

				INSERT INTO dbo.Operarios_histpuntoservicio (CodPuntoServicio,NombrePServicio,DireccionContrato,Barrios,Contacto,MailContacto,TelefonoContacto,Coordenadas,Ciudad_id,Cliente_id,NumeroMarcador,vfechaInicio,vfechaFin,vregistro,vactual_id,usuario_id,activo,comentario)
				VALUES(@p_CodPuntoServicio,@p_NombrePServicio,@p_DireccionContrato,@p_Barrios,@p_Contacto,@p_MailContacto,@p_TelefonoContacto,@p_Coordenadas,@p_Ciudad_id,@p_Cliente_id,@p_NumeroMarcador,@fechaCambio,NULL,@tmp1_vregistro+1,@p_id,@p_usuario,'True','');




			COMMIT TRANSACTION @TransactionName;
			SET @retorno=0;
	END TRY 
	BEGIN CATCH 
		print error_message();
		SELECT ERROR_MESSAGE() AS ErrorMessage
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;

	END CATCH

	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[reemplazo_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE       PROCEDURE [dbo].[reemplazo_manager]   
	@json_rem nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
			DECLARE @RC int;
			DECLARE @tmp nvarchar(max);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_rem);
			
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_rem)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[asignaciondet_tmptrg] @tmp,@retorno
				end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_rem);
	END CATCH
	Select @retorno as resultado;

END	
GO
/****** Object:  StoredProcedure [dbo].[reemplazocab_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE        PROCEDURE [dbo].[reemplazocab_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@p_id int,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
		
		SET NOCOUNT ON;
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @p_fechaCreacion datetime2;
		DECLARE @p_fechaHoraRemplazo datetime2 ;
		DECLARE @p_usuario_id int;
		DECLARE @p_alertaId_id int;
		DECLARE @p_tipoRemplazo nvarchar(max);

		
		Select @p_fechaInicio =convert(date,"value",103) from OpenJson(@json) where "key"='fechaInicio' and "value"!='None';
		Select @p_fechaFin =convert(date,"value",103) from OpenJson(@json) where "key"='fechaFin' and "value"!='None';
		Select @p_fechaHoraRemplazo ="value" from OpenJson(@json) where "key"='fechaHoraRemplazo' and "value"!='None';
		Select @p_usuario_id ="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
		Select @p_alertaId_id ="value" from OpenJson(@json) where "key"='alertaId_id' and "value"!='None';
		Select @p_tipoRemplazo =UPPER("value") from OpenJson(@json) where "key"='tipoRemplazo' and "value"!='None';
		set @p_fechaCreacion = CURRENT_TIMESTAMP
		UPDATE [dbo].[Operarios_remplazoscab]
		   SET [fechaInicio] = @p_fechaInicio
			  ,[fechaFin] = @p_fechaFin
			  ,[tipoRemplazo] = @p_tipoRemplazo
			  ,[usuario_id] = @p_usuario_id
			  ,[alertaId_id] = @p_alertaId_id
			  ,[fecha_creacion] = @p_fechaCreacion
		 WHERE id=@p_id

		

		SET @retorno=0;

END
GO
/****** Object:  StoredProcedure [dbo].[relevamiento_cab_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE   procedure [dbo].[relevamiento_cab_trg]   
  

	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;
		
		Declare @tmp1_vregistro int;
		DECLARE @dp0_id int;
		DECLARE @dp0_cantidad int;
		DECLARE @dp0_puntoServicio_id int;
		DECLARE @dp0_usuario_id int;
		DECLARE @dp0_tipoSalario_id int;
		DECLARE @dp0_cantAprendices int;
		DECLARE @dp0_id_tmp nvarchar(max);
		DECLARE @dp0_cantidadHrTotal nvarchar(max);
		DECLARE @dp0_cantidadHrEsp nvarchar(max);
		DECLARE @dp0_numCantidadHrTotal int;
		DECLARE @dp0_numCantidadHrEsp int;
		DECLARE @dp0_tipoSalario nvarchar(max);
		DECLARE @dp0_comentario nvarchar(max);
		DECLARE @dp0_estado nvarchar(max);
		DECLARE @dp0_fechaInicio date;
		DECLARE @dp0_fechaFin date;
		DECLARE @dp0_fecha datetime2;
		Declare @delete nvarchar(max);
		select @dp0_id_tmp="value" from OpenJson(@json) where "key"='id' and value!='None';
		select @dp0_fecha=cast("value"as date) from OpenJson(@json) where "key"='fechaInicio'  and value!='None';
		select @dp0_cantidad="value" from OpenJson(@json) where "key"='cantidad'  and value!='None';
		select @dp0_puntoServicio_id="value" from OpenJson(@json) where "key"='puntoServicio_id'  and value!='None';
		select @dp0_cantidadHrTotal="value" from OpenJson(@json) where "key"='cantidadHrTotal'  and value!='None';
		select @dp0_cantidadHrEsp="value" from OpenJson(@json) where "key"='cantidadHrEsp'  and value!='None';
		select @dp0_numCantidadHrTotal="value" from OpenJson(@json) where "key"='numCantidadHrTotal'  and value!='None';
		select @dp0_numCantidadHrEsp="value" from OpenJson(@json) where "key"='numCantidadHrEsp'  and value!='None';
		select @dp0_fechaInicio=cast("value"as date) from OpenJson(@json) where "key"='fechaInicio'  and value!='None';
		select @dp0_fechaFin=cast("value"as date) from OpenJson(@json) where "key"='fechaFin'  and value!='None';
		select @dp0_usuario_id="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
		select @dp0_tipoSalario="value" from OpenJson(@json) where "key"='tipoSalario'  and value!='None';
		select @dp0_comentario="value" from OpenJson(@json) where "key"='comentario'  and value!='None';
		select @dp0_cantAprendices="value" from OpenJson(@json) where "key"='cantAprendices'  and value!='None';
		select @dp0_estado="value" from OpenJson(@json) where "key"='estado'  and value!='None'; 
		if @dp0_estado is NULL
		begin
			SET @dp0_estado='Aprobado'
		end
		sELECT @dp0_tipoSalario_id=id from dbo.Operarios_tiposalario where tipoSalario like @dp0_tipoSalario
		if  @dp0_tipoSalario_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe tipo servicio');
		END
		
		if  @dp0_id_tmp  is not NULL and @dp0_id_tmp!='None'
		BEGIN
			select @dp0_id=cast(@dp0_id_tmp as int)
		END

		if  @dp0_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@dp0_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histrelevamientocab(fecha,cantidad,puntoServicio_id,cantidadHrTotal,
				cantidadHrEsp,fechaInicio,usuario_id,tipoSalario_id,comentario,cantAprendices,
				estado,fechaFin,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantidadHrEsp,numCantidadHrTotal)
				select fecha,cantidad,puntoServicio_id,cantidadHrTotal,
				cantidadHrEsp,fechaInicio,usuario_id,tipoSalario_id,comentario,cantAprendices,
				estado,fechaFin,@fechaCambio,NULL,@tmp1_vregistro,@dp0_id,numCantidadHrEsp,numCantidadHrTotal from dbo.Operarios_relevamientocab where id=@dp0_id;
			end

			update dbo.Operarios_histrelevamientocab set vfechaFin=@fechaCambio where vactual_id=@dp0_id and vregistro=@tmp1_vregistro;
			set @tmp1_vregistro=@tmp1_vregistro+1;
			INSERT INTO dbo.Operarios_histrelevamientocab(fecha,cantidad,puntoServicio_id,cantidadHrTotal,
				cantidadHrEsp,fechaInicio,usuario_id,tipoSalario_id,comentario,cantAprendices,
				estado,fechaFin,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantidadHrEsp,numCantidadHrTotal)
			select @dp0_fecha,@dp0_cantidad,@dp0_puntoServicio_id,@dp0_cantidadHrTotal,
				@dp0_cantidadHrEsp,@dp0_fechaInicio,@dp0_usuario_id,@dp0_tipoSalario_id,@dp0_comentario,@dp0_cantAprendices,
				@dp0_estado,@dp0_fechaFin,@fechaCambio,NULL,@tmp1_vregistro,@dp0_id,@dp0_numCantidadHrEsp,@dp0_numCantidadHrTotal

			update dbo.Operarios_relevamientocab set 
				fecha= @dp0_fecha,
				cantidad= @dp0_cantidad,
				puntoServicio_id= @dp0_puntoServicio_id,
				cantidadHrTotal= @dp0_cantidadHrTotal,
				cantidadHrEsp= @dp0_cantidadHrEsp,
				fechaInicio= @dp0_fechaInicio,
				usuario_id= @dp0_usuario_id,
				tipoSalario_id= @dp0_tipoSalario_id,
				comentario= @dp0_comentario,
				cantAprendices= @dp0_cantAprendices,
				estado= @dp0_estado,
				fechaFin= @dp0_fechaFin,
				numCantidadHrEsp=@dp0_numCantidadHrEsp,
				numCantidadHrTotal=@dp0_numCantidadHrTotal 
				where id=@dp0_id;
		end

		if  @dp0_id is NULL
		begin
			set @tmp1_vregistro=1;
			INSERT INTO dbo.Operarios_relevamientocab(fecha,cantidad,puntoServicio_id,cantidadHrTotal,
				cantidadHrEsp,fechaInicio,usuario_id,tipoSalario_id,comentario,cantAprendices,
				estado,fechaFin,numCantidadHrEsp,numCantidadHrTotal)
			select @dp0_fecha,@dp0_cantidad,@dp0_puntoServicio_id,@dp0_cantidadHrTotal,
				@dp0_cantidadHrEsp,@dp0_fechaInicio,@dp0_usuario_id,@dp0_tipoSalario_id,@dp0_comentario,@dp0_cantAprendices,
				@dp0_estado,@dp0_fechaFin,@dp0_numCantidadHrEsp,@dp0_numCantidadHrTotal;

			set @dp0_id=SCOPE_IDENTITY();

			INSERT INTO dbo.Operarios_histrelevamientocab(fecha,cantidad,puntoServicio_id,cantidadHrTotal,
				cantidadHrEsp,fechaInicio,usuario_id,tipoSalario_id,comentario,cantAprendices,
				estado,fechaFin,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantidadHrEsp,numCantidadHrTotal)
			select @dp0_fecha,@dp0_cantidad,@dp0_puntoServicio_id,@dp0_cantidadHrTotal,
				@dp0_cantidadHrEsp,@dp0_fechaInicio,@dp0_usuario_id,@dp0_tipoSalario_id,@dp0_comentario,@dp0_cantAprendices,
				@dp0_estado,@dp0_fechaFin,@fechaCambio,NULL,@tmp1_vregistro,@dp0_id,@dp0_numCantidadHrEsp,@dp0_numCantidadHrTotal
		end
		Select @retorno as resultado;

END		
GO
/****** Object:  StoredProcedure [dbo].[relevamiento_cabesp_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[relevamiento_cabesp_trg]   
  

	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;
		Declare @tmp1_vregistro int;
		DECLARE @dp0_id int;
		DECLARE @dp0_cantidad int;
		DECLARE @dp0_puntoServicio_id int;
		DECLARE @dp0_usuario_id int;
		DECLARE @dp0_cantAprendices int;
		DECLARE @dp0_id_tmp nvarchar(max);
		DECLARE @dp0_cantidadHrTotal nvarchar(max);
		DECLARE @dp0_cantidadHrEsp nvarchar(max);
		DECLARE @dp0_numCantidadHrTotal int;
		DECLARE @dp0_numCantidadHrEsp int;
		DECLARE @dp0_comentario nvarchar(max);
		DECLARE @dp0_estado nvarchar(max);
		Declare @delete nvarchar(max);
		select @dp0_id_tmp="value" from OpenJson(@json) where "key"='id' and value!='None';
		select @dp0_cantidad="value" from OpenJson(@json) where "key"='cantidad'and "value"!='None';
		select @dp0_puntoServicio_id="value" from OpenJson(@json) where "key"='puntoServicio_id' and "value"!='None';
		select @dp0_cantidadHrTotal="value" from OpenJson(@json) where "key"='cantidadHrTotal' and "value"!='None';
		select @dp0_cantidadHrEsp="value" from OpenJson(@json) where "key"='cantidadHrEsp' and "value"!='None';
		select @dp0_numCantidadHrTotal="value" from OpenJson(@json) where "key"='numCantidadHrTotal';
		select @dp0_numCantidadHrEsp="value" from OpenJson(@json) where "key"='numCantidadHrEsp';
		select @dp0_usuario_id="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
		select @dp0_estado="value" from OpenJson(@json) where "key"='estado' and "value"!='None';
		if @dp0_estado is NULL
		begin
			SET @dp0_estado='Aprobado'
		end
		if  @dp0_id_tmp  is not NULL and @dp0_id_tmp!='None'
		BEGIN
			select @dp0_id=cast(@dp0_id_tmp as int)
		END

		if  @dp0_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@dp0_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histrelevamientocab(fecha,cantidad,puntoServicio_id,cantidadHrTotal,
				cantidadHrEsp,fechaInicio,usuario_id,tipoSalario_id,comentario,cantAprendices,
				estado,fechaFin,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantidadHrEsp,numCantidadHrTotal)
				select fecha,cantidad,puntoServicio_id,cantidadHrTotal,
				cantidadHrEsp,fechaInicio,usuario_id,tipoSalario_id,comentario,cantAprendices,
				estado,fechaFin,@fechaCambio,NULL,@tmp1_vregistro,@dp0_id,numCantidadHrEsp,numCantidadHrTotal from dbo.Operarios_relevamientocab where id=@dp0_id;
			end

			update dbo.Operarios_histrelevamientocab set vfechaFin=@fechaCambio where vactual_id=@dp0_id and vregistro=@tmp1_vregistro;
			set @tmp1_vregistro=@tmp1_vregistro+1;
			INSERT INTO dbo.Operarios_histrelevamientocab(fecha,cantidad,puntoServicio_id,cantidadHrTotal,
				cantidadHrEsp,fechaInicio,usuario_id,tipoSalario_id,comentario,cantAprendices,
				estado,fechaFin,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantidadHrEsp,numCantidadHrTotal)
			select fecha,@dp0_cantidad,@dp0_puntoServicio_id,@dp0_cantidadHrTotal,
				@dp0_cantidadHrEsp,fechaInicio,@dp0_usuario_id,tipoSalario_id,@dp0_comentario,@dp0_cantAprendices,
				@dp0_estado,fechaFin,@fechaCambio,NULL,@tmp1_vregistro,@dp0_id,@dp0_numCantidadHrEsp,@dp0_numCantidadHrTotal from dbo.Operarios_relevamientocab where id=@dp0_id;

			update dbo.Operarios_relevamientocab set 
				cantidad= @dp0_cantidad,
				puntoServicio_id= @dp0_puntoServicio_id,
				cantidadHrTotal= @dp0_cantidadHrTotal,
				cantidadHrEsp= @dp0_cantidadHrEsp,
				usuario_id= @dp0_usuario_id,
				comentario= @dp0_comentario,
				cantAprendices= @dp0_cantAprendices,
				estado= @dp0_estado,
				numCantidadHrEsp=@dp0_numCantidadHrEsp,
				numCantidadHrTotal=@dp0_numCantidadHrTotal 
				where id=@dp0_id;
		end

		
		Select @retorno as resultado;

END		
GO
/****** Object:  StoredProcedure [dbo].[relevamiento_esp_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE     PROCEDURE [dbo].[relevamiento_esp_manager]   
	@json_cab nvarchar(max),
	@json_esp nvarchar(max),
	@retorno int OUTPUT
AS   
	
  BEGIN
  SET NOCOUNT ON;
	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
			DECLARE @RC int;
			DECLARE @cab int;
			DECLARE @tmp nvarchar(max);
			EXECUTE @RC = [dbo].[relevamiento_cab_trg] @json_cab,@fechaCambio,0
			/*ESP*/
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_esp)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[relevamientoesp_trg] @tmp,@fechaCambio,@retorno
					--EXECUTE @RC = [dbo].[generadorLimpieza] @tmp,@fechaCambio,@retorno
				end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt
			SET @retorno=0;
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_esp);
	END CATCH
	Select @retorno as resultado;

END		
GO
/****** Object:  StoredProcedure [dbo].[relevamiento_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE   PROCEDURE [dbo].[relevamiento_manager]   
	@json_cab nvarchar(max),
	@json_det nvarchar(max),
	@json_men nvarchar(max),
	@json_cup nvarchar(max),
	--@json_esp nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;
	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
			DECLARE @RC int;
			DECLARE @cab int;
			DECLARE @tmp nvarchar(max);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_det);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_men);
			insert into infolog(fechaHora,info) values(@fechaCambio,@json_cup);
			--insert into infolog(fechaHora,info) values(@fechaCambio,@json_esp);
			EXECUTE @RC = [dbo].[relevamiento_cab_trg] @json_cab,@fechaCambio,0
			/*det*/
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_det)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[relevamientodet_trg] @tmp,@fechaCambio,@retorno
				end



			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt
			/*ESP
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_esp)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[relevamientoesp_trg] @tmp,@fechaCambio,@retorno
				end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt*/
			/*MENSUALEROS*/
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_men)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[relevamientomensualeros_trg] @tmp,@fechaCambio,@retorno
				end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt


			/*CUPO HORAS*/
			DECLARE cursorIt CURSOR LOCAL FOR SELECT "value" FROM OpenJson(@json_cup)
			OPEN cursorIt
			FETCH NEXT FROM cursorIt INTO @tmp
			WHILE @@FETCH_STATUS = 0
			BEGIN
				IF @tmp is not NULL and @tmp!='{}'
				begin
					EXECUTE @RC = [dbo].[relevamientocupohoras_trg] @tmp,@fechaCambio,@retorno
				end
			FETCH NEXT FROM cursorIt INTO @tmp
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt
			SET @retorno=0;
		COMMIT TRANSACTION @TransactionName;
		SET @retorno=0;
	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		SET @retorno=1;
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_det);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_men);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_cup);
		--insert into infolog(fechaHora,info) values(@fechaCambio,@json_esp);
	END CATCH
	Select @retorno as resultado;

END		
GO
/****** Object:  StoredProcedure [dbo].[relevamientocupohoras_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE     PROCEDURE [dbo].[relevamientocupohoras_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_numCantHoras int;
		DECLARE @p_tipoHora nvarchar(max);
		DECLARE @p_cantHoras nvarchar(max);
		DECLARE @p_tipoHora_id int;
		DECLARE @p_relevamientocab_id int;
		DECLARE @p_frecuencia nvarchar(max);
		DECLARE @p_id int;
		DECLARE @p_sal time;
		DECLARE @p_ent time;
		DECLARE @p_fer bit ;
		DECLARE @p_dom bit ;
		DECLARE @p_sab bit ;
		DECLARE @p_vie bit ;
		DECLARE @p_jue bit ;
		DECLARE @p_mie bit ;
		DECLARE @p_mar bit ;
		DECLARE @p_lun bit ;
		select @p_dom="value" from OpenJson(@json) where "key"='dom';
		select @p_sab="value" from OpenJson(@json) where "key"='sab';
		select @p_vie="value" from OpenJson(@json) where "key"='vie';
		select @p_jue="value" from OpenJson(@json) where "key"='jue';
		select @p_mie="value" from OpenJson(@json) where "key"='mie';
		select @p_mar="value" from OpenJson(@json) where "key"='mar';
		select @p_lun="value" from OpenJson(@json) where "key"='lun';
		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @p_cantHoras="value" from OpenJson(@json) where "key"='cantCHoras'  and value!='None';
		select @p_numCantHoras="value" from OpenJson(@json) where "key"='numCantCHoras'  and value!='None';
		select @p_tipoHora_id="value" from OpenJson(@json) where "key"='tipoHora_id'  and value!='None';
		select @p_tipoHora="value" from OpenJson(@json) where "key"='tipoHora'  and value!='None';
		select @p_relevamientocab_id="value" from OpenJson(@json) where "key"='relevamientocab_id' and "value"!='None';
		select @p_frecuencia="value" from OpenJson(@json) where "key"='frecuencia'  and value!='None';
		select @p_id_tmp="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		
		sELECT @p_tipoHora_id=id from dbo.Operarios_tipohorario where tipoHorario like @p_tipoHora
		if  @p_tipoHora_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe tipo hORA');
		END


		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histrelevamientocupohoras(cantHoras,tipoHora_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,dom,sab,vie,jue,mie,mar,lun)
				select cantHoras,tipoHora_id,relevamientocab_id,frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_dom,@p_sab,@p_vie,@p_jue,@p_mie,@p_mar,@p_lun from dbo.Operarios_relevamientocupohoras where id=@p_id;
			end
			update dbo.Operarios_histrelevamientocupohoras set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				INSERT INTO dbo.Operarios_histrelevamientocupohoras(cantHoras,tipoHora_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,dom,sab,vie,jue,mie,mar,lun)
				select @p_cantHoras,@p_tipoHora_id,@p_relevamientocab_id,@p_frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_dom,@p_sab,@p_vie,@p_jue,@p_mie,@p_mar,@p_lun
				update dbo.Operarios_relevamientocupohoras set 
					 cantHoras=@p_cantHoras,tipoHora_id=@p_tipoHora_id,relevamientocab_id=@p_relevamientocab_id,
					 frecuencia=@p_frecuencia,numCantHoras=@p_numCantHoras,
					 dom=@p_dom,sab=@p_sab,vie=@p_vie,jue=@p_jue,mie=@p_mie,mar=@p_mar,lun=@p_lun
					 where id=@p_id;
			end
			if @delete is not NULL and @delete='True'
			begin
       	update Operarios_histrelevamientocupohoras set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_relevamientocupohoras  where id=@p_id;
			end

		end


		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			INSERT INTO dbo.Operarios_relevamientocupohoras(cantHoras,tipoHora_id,relevamientocab_id,frecuencia,numCantHoras,dom,sab,vie,jue,mie,mar,lun)
			select @p_cantHoras,@p_tipoHora_id,@p_relevamientocab_id,@p_frecuencia,@p_numCantHoras,@p_dom,@p_sab,@p_vie,@p_jue,@p_mie,@p_mar,@p_lun;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histrelevamientocupohoras(cantHoras,tipoHora_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,dom,sab,vie,jue,mie,mar,lun)
			select @p_cantHoras,@p_tipoHora_id,@p_relevamientocab_id,@p_frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_dom,@p_sab,@p_vie,@p_jue,@p_mie,@p_mar,@p_lun
		end
		SET @retorno=0;
		Select @retorno as resultado;
END

GO
/****** Object:  StoredProcedure [dbo].[relevamientodet_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[relevamientodet_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_tipoServPart_id int;
		DECLARE @p_relevamientocab_id int;
		DECLARE @p_domSal time;
		DECLARE @p_domEnt time;
		DECLARE @p_sabSal time;
		DECLARE @p_sabEnt time;
		DECLARE @p_vieSal time;
		DECLARE @p_vieEnt time;
		DECLARE @p_jueSal time;
		DECLARE @p_jueEnt time;
		DECLARE @p_mieSal time;
		DECLARE @p_mieEnt time;
		DECLARE @p_marSal time;
		DECLARE @p_marEnt time;
		DECLARE @p_lunSal time;
		DECLARE @p_lunEnt time;
		DECLARE @p_orden int;
		DECLARE @p_id int;
		declare @p_tipoServPart nvarchar(max);

		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @p_tipoServPart_id="value" from OpenJson(@json) where "key"='tipoServPart_id'  and value!='None';
		select @p_tipoServPart="value" from OpenJson(@json) where "key"='tipoServPart'  and value!='None';
		select @p_relevamientocab_id="value" from OpenJson(@json) where "key"='relevamientocab_id' and "value"!='None';
		select @p_domSal="value" from OpenJson(@json) where "key"='domSal' and "value"!='None';
		select @p_domEnt="value" from OpenJson(@json) where "key"='domEnt' and "value"!='None';
		select @p_sabSal="value" from OpenJson(@json) where "key"='sabSal' and "value"!='None';
		select @p_sabEnt="value" from OpenJson(@json) where "key"='sabEnt' and "value"!='None';
		select @p_vieSal="value" from OpenJson(@json) where "key"='vieSal' and "value"!='None';
		select @p_vieEnt="value" from OpenJson(@json) where "key"='vieEnt' and "value"!='None';
		select @p_jueSal="value" from OpenJson(@json) where "key"='jueSal' and "value"!='None';
		select @p_jueEnt="value" from OpenJson(@json) where "key"='jueEnt' and "value"!='None';
		select @p_mieSal="value" from OpenJson(@json) where "key"='mieSal' and "value"!='None';
		select @p_mieEnt="value" from OpenJson(@json) where "key"='mieEnt' and "value"!='None';
		select @p_marSal="value" from OpenJson(@json) where "key"='marSal' and "value"!='None';
		select @p_marEnt="value" from OpenJson(@json) where "key"='marEnt' and "value"!='None';
		select @p_lunSal="value" from OpenJson(@json) where "key"='lunSal' and "value"!='None';
		select @p_lunEnt="value" from OpenJson(@json) where "key"='lunEnt' and "value"!='None';
		select @p_orden="value" from OpenJson(@json) where "key"='orden' and "value"!='None';
		select @p_id_tmp="value" from OpenJson(@json) where "key"='id' and "value"!='None';

		sELECT @p_tipoServPart_id=id from dbo.Operarios_tiposervicioparticular where tipoServicioParticular like @p_tipoServPart
		if  @p_tipoServPart_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe tipo servicio particular');
		END

		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END


		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=@retorno-1;
				INSERT INTO dbo.Operarios_histrelevamientodet(tipoServPart_id,relevamientocab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,orden,vfechaInicio,vfechaFin,vregistro,vactual_id)
				select tipoServPart_id,relevamientocab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,orden,@fechaCambio,NULL,@tmp1_vregistro,@p_id from dbo.Operarios_relevamientodet where id=@p_id;
			end
			
			update dbo.Operarios_histrelevamientodet set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				INSERT INTO dbo.Operarios_histrelevamientodet(tipoServPart_id,relevamientocab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,orden,vfechaInicio,vfechaFin,vregistro,vactual_id)
				select @p_tipoServPart_id,@p_relevamientocab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@p_orden,@fechaCambio,NULL,@tmp1_vregistro,@p_id
				update dbo.Operarios_relevamientodet set 
					 tipoServPart_id=@p_tipoServPart_id,relevamientocab_id=@p_relevamientocab_id,domSal=@p_domSal,domEnt=@p_domEnt,sabSal=@p_sabSal,sabEnt=@p_sabEnt,vieSal=@p_vieSal,vieEnt=@p_vieEnt,jueSal=@p_jueSal,jueEnt=@p_jueEnt,mieSal=@p_mieSal,mieEnt=@p_mieEnt,marSal=@p_marSal,marEnt=@p_marEnt,lunSal=@p_lunSal,lunEnt=@p_lunEnt,orden=@p_orden where id=@p_id;
			end
			if @delete is not NULL and @delete='True'
			begin
				update Operarios_histrelevamientodet set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_relevamientodet  where id=@p_id;
			end
		end


		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			INSERT INTO dbo.Operarios_relevamientodet(tipoServPart_id,relevamientocab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,orden)
			select @p_tipoServPart_id,@p_relevamientocab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@p_orden;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histrelevamientodet(tipoServPart_id,relevamientocab_id,domSal,domEnt,sabSal,sabEnt,vieSal,vieEnt,jueSal,jueEnt,mieSal,mieEnt,marSal,marEnt,lunSal,lunEnt,orden,vfechaInicio,vfechaFin,vregistro,vactual_id)
			select @p_tipoServPart_id,@p_relevamientocab_id,@p_domSal,@p_domEnt,@p_sabSal,@p_sabEnt,@p_vieSal,@p_vieEnt,@p_jueSal,@p_jueEnt,@p_mieSal,@p_mieEnt,@p_marSal,@p_marEnt,@p_lunSal,@p_lunEnt,@p_orden,@fechaCambio,NULL,@tmp1_vregistro,@p_id
		end
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[relevamientoesp_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE   procedure [dbo].[relevamientoesp_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_cantHoras nvarchar(max);
		DECLARE @p_sector nvarchar(max);
		DECLARE @p_area nvarchar(max);
		DECLARE @p_tipo_hora_id int;
		DECLARE @p_tipo_hora nvarchar(max);
		DECLARE @p_perfil nvarchar(max);
		DECLARE @p_perfil_id int;
		DECLARE @p_cantidad int;
		DECLARE @p_numCantHoras int;
		DECLARE @p_tipo_id int;
		DECLARE @p_relevamientocab_id int;
		DECLARE @p_frecuencia nvarchar(max);
		DECLARE @p_id int;
		declare @p_tipo nvarchar(max);

		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @p_cantHoras="value" from OpenJson(@json) where "key"='cantHoras';
		select @p_sector="value" from OpenJson(@json) where "key"='sector';
		select @p_area="value" from OpenJson(@json) where "key"='area';
		select @p_cantidad=cast("value" as int) from OpenJson(@json) where "key"='cantidad' and "value"!='None';
		
		select @p_perfil="value" from OpenJson(@json) where "key"='perfil';
		select @p_tipo_hora="value" from OpenJson(@json) where "key"='tipoHora';
		
		select @p_numCantHoras="value" from OpenJson(@json) where "key"='numCantHoras';
		select @p_tipo_id="value" from OpenJson(@json) where "key"='tipo_id';
		select @p_tipo="value" from OpenJson(@json) where "key"='tipoServicio';
		select @p_relevamientocab_id="value" from OpenJson(@json) where "key"='relevamientocab_id' and "value"!='None';
		select @p_frecuencia="value" from OpenJson(@json) where "key"='frecuencia';
		select @p_id_tmp="value" from OpenJson(@json) where "key"='id' and "value"!='None';

		sELECT @p_tipo_id=id from dbo.Operarios_tiposervicio where tipoServicio like @p_tipo
		if  @p_tipo_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe tipo servicio particular');
		END

		sELECT @p_perfil_id=id from dbo.Operarios_especializacion where especializacion like @p_perfil
		if  @p_perfil_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe especialidad');
		END

		sELECT @p_tipo_hora_id=id from dbo.Operarios_tipohorario where tipoHorario like @p_tipo_hora
		if  @p_tipo_hora_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe tipo de hora');
		END

		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histrelevamientoesp(cantHoras,tipo_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,sector,area,cantidad,perfil_id,tipoHora_id)
				select cantHoras,tipo_id,relevamientocab_id,frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_sector,@p_area,@p_cantidad,@p_perfil_id,@p_tipo_hora_id from dbo.Operarios_relevamientoesp where id=@p_id;
			end
			update dbo.Operarios_histrelevamientoesp set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				INSERT INTO dbo.Operarios_histrelevamientoesp(cantHoras,tipo_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,sector,area,cantidad,perfil_id,tipoHora_id)
				select @p_cantHoras,@p_tipo_id,@p_relevamientocab_id,@p_frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_sector,@p_area,@p_cantidad,@p_perfil_id,@p_tipo_hora_id
				update dbo.Operarios_relevamientoesp set 
					 cantHoras=@p_cantHoras,tipo_id=@p_tipo_id,relevamientocab_id=@p_relevamientocab_id,
					 frecuencia=@p_frecuencia,numCantHoras=@p_numCantHoras
					 ,sector=@p_sector
					 ,area=@p_area
					 ,cantidad=@p_cantidad
					 ,perfil_id=@p_perfil_id
					 ,tipoHora_id=@p_tipo_hora_id
					 where id=@p_id;
			end
			if @delete is not NULL and @delete='True'
			begin
				update Operarios_histrelevamientoesp set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_relevamientoesp  where id=@p_id;
				
			end
		end


		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			INSERT INTO dbo.Operarios_relevamientoesp(cantHoras,tipo_id,relevamientocab_id,frecuencia,numCantHoras,sector,area,cantidad,perfil_id,tipoHora_id)
			select @p_cantHoras,@p_tipo_id,@p_relevamientocab_id,@p_frecuencia,@p_numCantHoras,@p_sector,@p_area,@p_cantidad,@p_perfil_id,@p_tipo_hora_id;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histrelevamientoesp(cantHoras,tipo_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,sector,area,cantidad,perfil_id,tipoHora_id)
			select @p_cantHoras,@p_tipo_id,@p_relevamientocab_id,@p_frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_sector,@p_area,@p_cantidad,@p_perfil_id,@p_tipo_hora_id
		end
		SET @retorno=0;
		Select @retorno as resultado;
END

GO
/****** Object:  StoredProcedure [dbo].[relevamientoesp_unico_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE         PROCEDURE [dbo].[relevamientoesp_unico_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_cantHoras nvarchar(max);
		DECLARE @p_sector nvarchar(max);
		DECLARE @p_area nvarchar(max);
		DECLARE @p_tipo_hora_id int;
		DECLARE @p_tipo_hora nvarchar(max);
		DECLARE @p_perfil nvarchar(max);
		DECLARE @p_perfil_id int;
		DECLARE @p_cantidad int;
		DECLARE @p_numCantHoras int;
		DECLARE @p_tipo_id int;
		DECLARE @p_relevamientocab_id int;
		DECLARE @p_frecuencia nvarchar(max);
		DECLARE @p_id int;
		declare @p_tipo nvarchar(max);
		--select 'entre al unico'
		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @p_cantHoras="value" from OpenJson(@json) where "key"='cantHoras';
		select @p_sector="value" from OpenJson(@json) where "key"='sector';
		select @p_area="value" from OpenJson(@json) where "key"='area';
		select @p_cantidad=cast("value" as int) from OpenJson(@json) where "key"='cantidad' and "value"!='None';
		
		select @p_perfil="value" from OpenJson(@json) where "key"='perfil';
		select @p_tipo_hora="value" from OpenJson(@json) where "key"='tipoHora';
		
		select @p_numCantHoras="value" from OpenJson(@json) where "key"='numCantHoras';
		select @p_tipo_id="value" from OpenJson(@json) where "key"='tipo_id';
		select @p_tipo="value" from OpenJson(@json) where "key"='tipoServicio';
		select @p_relevamientocab_id="value" from OpenJson(@json) where "key"='relevamientocab_id' and "value"!='None';
		select @p_frecuencia="value" from OpenJson(@json) where "key"='frecuencia';
		select @p_id_tmp="value" from OpenJson(@json) where "key"='id' and "value"!='None';

		sELECT @p_tipo_id=id from dbo.Operarios_tiposervicio where tipoServicio like @p_tipo
		if  @p_tipo_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe tipo servicio particular');
		END

		sELECT @p_perfil_id=id from dbo.Operarios_especializacion where especializacion like @p_perfil
		if  @p_perfil_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe especialidad');
		END

		sELECT @p_tipo_hora_id=id from dbo.Operarios_tipohorario where tipoHorario like @p_tipo_hora
		if  @p_tipo_hora_id is NULL
		BEGIN
			RAISERROR(15000,0,0,'NO existe tipo de hora');
		END

		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histrelevamientoesp(cantHoras,tipo_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,sector,area,cantidad,perfil_id,tipoHora_id)
				select cantHoras,tipo_id,relevamientocab_id,frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_sector,@p_area,@p_cantidad,@p_perfil_id,@p_tipo_hora_id from dbo.Operarios_relevamientoesp where id=@p_id;
			end
			update dbo.Operarios_histrelevamientoesp set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				INSERT INTO dbo.Operarios_histrelevamientoesp(cantHoras,tipo_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,sector,area,cantidad,perfil_id,tipoHora_id)
				select @p_cantHoras,@p_tipo_id,@p_relevamientocab_id,@p_frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_sector,@p_area,@p_cantidad,@p_perfil_id,@p_tipo_hora_id
				update dbo.Operarios_relevamientoesp set 
					 cantHoras=@p_cantHoras,tipo_id=@p_tipo_id,relevamientocab_id=@p_relevamientocab_id,
					 frecuencia=@p_frecuencia,numCantHoras=@p_numCantHoras
					 ,sector=@p_sector
					 ,area=@p_area
					 ,cantidad=@p_cantidad
					 ,perfil_id=@p_perfil_id
					 ,tipoHora_id=@p_tipo_hora_id
					 where id=@p_id;
			end
			if @delete is not NULL and @delete='True'
			begin
				update Operarios_histrelevamientoesp set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_relevamientoesp  where id=@p_id;
				
			end
		end


		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			INSERT INTO dbo.Operarios_relevamientoesp(cantHoras,tipo_id,relevamientocab_id,frecuencia,numCantHoras,sector,area,cantidad,perfil_id,tipoHora_id)
			select @p_cantHoras,@p_tipo_id,@p_relevamientocab_id,@p_frecuencia,@p_numCantHoras,@p_sector,@p_area,@p_cantidad,@p_perfil_id,@p_tipo_hora_id;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histrelevamientoesp(cantHoras,tipo_id,relevamientocab_id,frecuencia,vfechaInicio,vfechaFin,vregistro,vactual_id,numCantHoras,sector,area,cantidad,perfil_id,tipoHora_id)
			select @p_cantHoras,@p_tipo_id,@p_relevamientocab_id,@p_frecuencia,@fechaCambio,NULL,@tmp1_vregistro,@p_id,@p_numCantHoras,@p_sector,@p_area,@p_cantidad,@p_perfil_id,@p_tipo_hora_id
		end
		SET @retorno=0;
		Select @retorno as resultado;
END

GO
/****** Object:  StoredProcedure [dbo].[relevamientomensualeros_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE       PROCEDURE [dbo].[relevamientomensualeros_trg]   
	@json nvarchar(max),
	@fechaCambio datetime,
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
	SET NOCOUNT ON;
		
		DECLARE @tmp1_vregistro int;
		DECLARE @p_id_tmp nvarchar(max);
		DECLARE @p_fechaInicio date;
		DECLARE @p_fechaFin date;
		DECLARE @delete nvarchar(max);
		DECLARE @p_sueldo int;
		DECLARE @p_mensuCantidad int;
		DECLARE @p_relevamientocab_id int;
		DECLARE @p_id int;

		select @delete="value" from OpenJson(@json) where "key"='DELETE';
		select @p_sueldo="value" from OpenJson(@json) where "key"='sueldo' and "value"!='None';
		select @p_mensuCantidad="value" from OpenJson(@json) where "key"='mensuCantidad' and "value"!='None';
		select @p_relevamientocab_id="value" from OpenJson(@json) where "key"='relevamientocab_id' and "value"!='None';
		select @p_id_tmp="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		if  @p_id_tmp  is not NULL and @p_id_tmp!='None'
		BEGIN
			select @p_id=cast(@p_id_tmp as int)
		END
		if  @p_id is not NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			if @tmp1_vregistro is NULL
			begin
				set @tmp1_vregistro=1;
				INSERT INTO dbo.Operarios_histrelevamientomensualeros(sueldo,mensuCantidad,relevamientocab_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
				select sueldo,mensuCantidad,relevamientocab_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id from dbo.Operarios_relevamientomensualeros where id=@p_id;
			end
			update dbo.Operarios_histrelevamientomensualeros set vfechaFin=@fechaCambio where vactual_id=@p_id and vregistro=@tmp1_vregistro-1;
			if @delete is not NULL and @delete='False'
			begin
				INSERT INTO dbo.Operarios_histrelevamientomensualeros(sueldo,mensuCantidad,relevamientocab_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
				select @p_sueldo,@p_mensuCantidad,@p_relevamientocab_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id
				update dbo.Operarios_relevamientomensualeros set 
					 sueldo=@p_sueldo,mensuCantidad=@p_mensuCantidad,relevamientocab_id=@p_relevamientocab_id where id=@p_id;
			end
			if @delete is not NULL and @delete='True'
			begin
        update Operarios_histrelevamientomensualeros set vactual_id=NULL where vactual_id=@p_id;
				delete from dbo.Operarios_relevamientomensualeros  where id=@p_id;
			end
		end


		if  @p_id is NULL
		begin
			select @tmp1_vregistro=max(vregistro) from dbo.Operarios_histrelevamientocab where vactual_id=@p_relevamientocab_id;
			INSERT INTO dbo.Operarios_relevamientomensualeros(sueldo,mensuCantidad,relevamientocab_id)
			select @p_sueldo,@p_mensuCantidad,@p_relevamientocab_id;
			set @p_id=SCOPE_IDENTITY();
			INSERT INTO dbo.Operarios_histrelevamientomensualeros(sueldo,mensuCantidad,relevamientocab_id,vfechaInicio,vfechaFin,vregistro,vactual_id)
			select @p_sueldo,@p_mensuCantidad,@p_relevamientocab_id,@fechaCambio,NULL,@tmp1_vregistro,@p_id
		end
		SET @retorno=0;
		Select @retorno as resultado;
END
GO
/****** Object:  StoredProcedure [dbo].[remp_manual_save_trg]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE          PROCEDURE [dbo].[remp_manual_save_trg]   
	@json nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
	BEGIN
		SET NOCOUNT ON;
		DECLARE @p_id int;
		declare @p_hora time;
		declare @p_motivo_id int;
		declare @p_fechaRetorno datetime;
		declare @p_comentarios nvarchar(max);
		declare @p_usuario_id int;
		declare @p_id_reemplazo_id int;
		declare @p_fecha_creacion datetime2;

		
		Select @p_id ="value" from OpenJson(@json) where "key"='id' and "value"!='None';
		select @p_hora ="value" from OpenJson(@json) where "key"='hora' and "value"!='None';
		select @p_motivo_id ="value" from OpenJson(@json) where "key"='motivo_id' and "value"!='None';
		select @p_fechaRetorno =convert(datetime,"value",120) from OpenJson(@json) where "key"='fechaRetorno' and "value"!='None';
		select @p_comentarios ="value" from OpenJson(@json) where "key"='comentarios' and "value"!='None';
		select @p_usuario_id ="value" from OpenJson(@json) where "key"='usuario_id' and "value"!='None';
		select @p_id_reemplazo_id ="value" from OpenJson(@json) where "key"='reemplazo_id' and "value"!='None';
		set @p_fecha_creacion = CURRENT_TIMESTAMP
		

		INSERT INTO [dbo].[Operarios_remplazomanresp]
           ([fechaRetorno]
           ,[comentarios]
           ,[fecha_creacion]
           ,[id_reemplazo_id]
           ,[motivo_id]
           ,[usuario_id])
		VALUES
           (@p_fechaRetorno
           ,@p_comentarios
           ,@p_fecha_creacion
           ,@p_id_reemplazo_id
           ,@p_motivo_id
           ,@p_usuario_id);

		SET @retorno=0;
		
END
GO
/****** Object:  StoredProcedure [dbo].[remp_save_manager]    Script Date: 19/12/2019 15:07:19 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

CREATE         PROCEDURE [dbo].[remp_save_manager]   
	@json_cab nvarchar(max),
	@remp_cab int,
	@json_alrm nvarchar(max),
	@json_rman nvarchar(max),
	@retorno int OUTPUT
	--@operario int
AS   
	
  BEGIN
  SET NOCOUNT ON;

	DECLARE @TransactionName varchar(20) = 'Transactional';
	Declare @err_msg nvarchar(max);
	BEGIN TRAN @TransactionName 
	BEGIN TRY
		DECLARE @fechaCambio datetime;
		SET @fechaCambio=CURRENT_TIMESTAMP;
		declare @p_fechaInicio date;
		declare @p_fechaFin date;
		declare @p_operario_id int;
		declare @p_ps_id int;
		declare @p_asignacionDet_original_id int;
		declare @p_remplazosCab_id int;
		DECLARE @RC int;
		DECLARE @tmp int;
			
		EXECUTE @RC = [dbo].[reemplazocab_trg] @json_cab,@fechaCambio,@remp_cab,@retorno
		
		
		DECLARE cursorIt CURSOR LOCAL FOR SELECT fechaInicio,fechaFin,operario_id,asignacionDet_original_id,remplazosCab_id from Operarios_asignaciondettemp where remplazosCab_id=@remp_cab and (eliminado='False' or eliminado is NULL)
		OPEN cursorIt
		FETCH NEXT FROM cursorIt INTO @p_fechaInicio,@p_fechaFin,@p_operario_id,@p_asignacionDet_original_id,@p_remplazosCab_id
		WHILE @@FETCH_STATUS = 0
		BEGIN
			select @p_ps_id=ac.puntoServicio_id from dbo.Operarios_asignaciondet ad 
			inner join dbo.Operarios_asignacioncab ac on ac.id=ad.asignacionCab_id where ad.id=@p_asignacionDet_original_id;
			
			INSERT INTO [dbo].[Operarios_remplazosdet] (fecha,fechaFin,Asignacion_id,remplazo_id,remplazoCab_id,diaRemplazo,puntoServicio_id)
			VALUES (@p_fechaInicio,@p_fechaFin,@p_asignacionDet_original_id,@p_operario_id,@p_remplazosCab_id,'',@p_ps_id);

			FETCH NEXT FROM cursorIt INTO @p_fechaInicio,@p_fechaFin,@p_operario_id,@p_asignacionDet_original_id,@p_remplazosCab_id
			END
			CLOSE cursorIt
			DEALLOCATE cursorIt

			delete from dbo.Operarios_asignaciondettemp where remplazosCab_id=@remp_cab;
			if @json_alrm != '' 
			begin
				EXECUTE @RC = [dbo].[alertasave_trg] @json_alrm,@retorno;
			end
			if @json_rman != '' 
			begin
				EXECUTE @RC = [dbo].[remp_manual_save_trg] @json_rman,@retorno;
			end
			

			SET @RC=0;
		COMMIT TRANSACTION @TransactionName;

	END TRY 
	BEGIN CATCH
		set @err_msg=ERROR_MESSAGE();
		ROLLBACK TRAN @TransactionName; 
		set @RC=1;
		insert into dbo.infolog(fechaHora,info) values(current_timestamp, @err_msg);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_cab);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_alrm);
		insert into infolog(fechaHora,info) values(@fechaCambio,@json_rman);
	END CATCH
	
	SELECT @retorno=@RC;
	select @retorno as resultado;
	RETURN @retorno;
END	

GO
EXEC sys.sp_addextendedproperty @name=N'MS_DiagramPane1', @value=N'[0E232FF0-B466-11cf-A24F-00AA00A3EFFF, 1.00]
Begin DesignProperties = 
   Begin PaneConfigurations = 
      Begin PaneConfiguration = 0
         NumPanes = 4
         Configuration = "(H (1[40] 4[20] 2[20] 3) )"
      End
      Begin PaneConfiguration = 1
         NumPanes = 3
         Configuration = "(H (1 [50] 4 [25] 3))"
      End
      Begin PaneConfiguration = 2
         NumPanes = 3
         Configuration = "(H (1 [50] 2 [25] 3))"
      End
      Begin PaneConfiguration = 3
         NumPanes = 3
         Configuration = "(H (4 [30] 2 [40] 3))"
      End
      Begin PaneConfiguration = 4
         NumPanes = 2
         Configuration = "(H (1 [56] 3))"
      End
      Begin PaneConfiguration = 5
         NumPanes = 2
         Configuration = "(H (2 [66] 3))"
      End
      Begin PaneConfiguration = 6
         NumPanes = 2
         Configuration = "(H (4 [50] 3))"
      End
      Begin PaneConfiguration = 7
         NumPanes = 1
         Configuration = "(V (3))"
      End
      Begin PaneConfiguration = 8
         NumPanes = 3
         Configuration = "(H (1[56] 4[18] 2) )"
      End
      Begin PaneConfiguration = 9
         NumPanes = 2
         Configuration = "(H (1 [75] 4))"
      End
      Begin PaneConfiguration = 10
         NumPanes = 2
         Configuration = "(H (1[66] 2) )"
      End
      Begin PaneConfiguration = 11
         NumPanes = 2
         Configuration = "(H (4 [60] 2))"
      End
      Begin PaneConfiguration = 12
         NumPanes = 1
         Configuration = "(H (1) )"
      End
      Begin PaneConfiguration = 13
         NumPanes = 1
         Configuration = "(V (4))"
      End
      Begin PaneConfiguration = 14
         NumPanes = 1
         Configuration = "(V (2))"
      End
      ActivePaneConfig = 0
   End
   Begin DiagramPane = 
      Begin Origin = 
         Top = 0
         Left = 0
      End
      Begin Tables = 
         Begin Table = "op_1"
            Begin Extent = 
               Top = 6
               Left = 38
               Bottom = 136
               Right = 252
            End
            DisplayFlags = 280
            TopColumn = 0
         End
      End
   End
   Begin SQLPane = 
   End
   Begin DataPane = 
      Begin ParameterDefaults = ""
      End
   End
   Begin CriteriaPane = 
      Begin ColumnWidths = 11
         Column = 1440
         Alias = 900
         Table = 1170
         Output = 720
         Append = 1400
         NewValue = 1170
         SortType = 1350
         SortOrder = 1410
         GroupBy = 1350
         Filter = 1350
         Or = 1350
         Or = 1350
         Or = 1350
      End
   End
End
' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'VIEW',@level1name=N'detalle_lista_operarios'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_DiagramPaneCount', @value=1 , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'VIEW',@level1name=N'detalle_lista_operarios'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_DiagramPane1', @value=N'[0E232FF0-B466-11cf-A24F-00AA00A3EFFF, 1.00]
Begin DesignProperties = 
   Begin PaneConfigurations = 
      Begin PaneConfiguration = 0
         NumPanes = 4
         Configuration = "(H (1[41] 4[20] 2[28] 3) )"
      End
      Begin PaneConfiguration = 1
         NumPanes = 3
         Configuration = "(H (1 [50] 4 [25] 3))"
      End
      Begin PaneConfiguration = 2
         NumPanes = 3
         Configuration = "(H (1 [50] 2 [25] 3))"
      End
      Begin PaneConfiguration = 3
         NumPanes = 3
         Configuration = "(H (4 [30] 2 [40] 3))"
      End
      Begin PaneConfiguration = 4
         NumPanes = 2
         Configuration = "(H (1 [56] 3))"
      End
      Begin PaneConfiguration = 5
         NumPanes = 2
         Configuration = "(H (2 [66] 3))"
      End
      Begin PaneConfiguration = 6
         NumPanes = 2
         Configuration = "(H (4 [50] 3))"
      End
      Begin PaneConfiguration = 7
         NumPanes = 1
         Configuration = "(V (3))"
      End
      Begin PaneConfiguration = 8
         NumPanes = 3
         Configuration = "(H (1[56] 4[18] 2) )"
      End
      Begin PaneConfiguration = 9
         NumPanes = 2
         Configuration = "(H (1 [75] 4))"
      End
      Begin PaneConfiguration = 10
         NumPanes = 2
         Configuration = "(H (1[66] 2) )"
      End
      Begin PaneConfiguration = 11
         NumPanes = 2
         Configuration = "(H (4 [60] 2))"
      End
      Begin PaneConfiguration = 12
         NumPanes = 1
         Configuration = "(H (1) )"
      End
      Begin PaneConfiguration = 13
         NumPanes = 1
         Configuration = "(V (4))"
      End
      Begin PaneConfiguration = 14
         NumPanes = 1
         Configuration = "(V (2))"
      End
      ActivePaneConfig = 0
   End
   Begin DiagramPane = 
      Begin Origin = 
         Top = -288
         Left = 0
      End
      Begin Tables = 
         Begin Table = "op_1"
            Begin Extent = 
               Top = 294
               Left = 38
               Bottom = 424
               Right = 268
            End
            DisplayFlags = 280
            TopColumn = 0
         End
      End
   End
   Begin SQLPane = 
   End
   Begin DataPane = 
      Begin ParameterDefaults = ""
      End
   End
   Begin CriteriaPane = 
      Begin ColumnWidths = 11
         Column = 1440
         Alias = 900
         Table = 1170
         Output = 720
         Append = 1400
         NewValue = 1170
         SortType = 1350
         SortOrder = 1410
         GroupBy = 1350
         Filter = 1350
         Or = 1350
         Or = 1350
         Or = 1350
      End
   End
End
' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'VIEW',@level1name=N'detalle_lista_operarios2'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_DiagramPaneCount', @value=1 , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'VIEW',@level1name=N'detalle_lista_operarios2'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_DiagramPane1', @value=N'[0E232FF0-B466-11cf-A24F-00AA00A3EFFF, 1.00]
Begin DesignProperties = 
   Begin PaneConfigurations = 
      Begin PaneConfiguration = 0
         NumPanes = 4
         Configuration = "(H (1[40] 4[20] 2[20] 3) )"
      End
      Begin PaneConfiguration = 1
         NumPanes = 3
         Configuration = "(H (1 [50] 4 [25] 3))"
      End
      Begin PaneConfiguration = 2
         NumPanes = 3
         Configuration = "(H (1 [50] 2 [25] 3))"
      End
      Begin PaneConfiguration = 3
         NumPanes = 3
         Configuration = "(H (4 [30] 2 [40] 3))"
      End
      Begin PaneConfiguration = 4
         NumPanes = 2
         Configuration = "(H (1 [56] 3))"
      End
      Begin PaneConfiguration = 5
         NumPanes = 2
         Configuration = "(H (2 [66] 3))"
      End
      Begin PaneConfiguration = 6
         NumPanes = 2
         Configuration = "(H (4 [50] 3))"
      End
      Begin PaneConfiguration = 7
         NumPanes = 1
         Configuration = "(V (3))"
      End
      Begin PaneConfiguration = 8
         NumPanes = 3
         Configuration = "(H (1[56] 4[18] 2) )"
      End
      Begin PaneConfiguration = 9
         NumPanes = 2
         Configuration = "(H (1 [75] 4))"
      End
      Begin PaneConfiguration = 10
         NumPanes = 2
         Configuration = "(H (1[66] 2) )"
      End
      Begin PaneConfiguration = 11
         NumPanes = 2
         Configuration = "(H (4 [60] 2))"
      End
      Begin PaneConfiguration = 12
         NumPanes = 1
         Configuration = "(H (1) )"
      End
      Begin PaneConfiguration = 13
         NumPanes = 1
         Configuration = "(V (4))"
      End
      Begin PaneConfiguration = 14
         NumPanes = 1
         Configuration = "(V (2))"
      End
      ActivePaneConfig = 0
   End
   Begin DiagramPane = 
      Begin Origin = 
         Top = 0
         Left = 0
      End
      Begin Tables = 
         Begin Table = "op_1"
            Begin Extent = 
               Top = 6
               Left = 38
               Bottom = 136
               Right = 252
            End
            DisplayFlags = 280
            TopColumn = 0
         End
      End
   End
   Begin SQLPane = 
   End
   Begin DataPane = 
      Begin ParameterDefaults = ""
      End
      Begin ColumnWidths = 9
         Width = 284
         Width = 1500
         Width = 1500
         Width = 1500
         Width = 1500
         Width = 1500
         Width = 1500
         Width = 1500
         Width = 1500
      End
   End
   Begin CriteriaPane = 
      Begin ColumnWidths = 11
         Column = 1440
         Alias = 900
         Table = 1170
         Output = 720
         Append = 1400
         NewValue = 1170
         SortType = 1350
         SortOrder = 1410
         GroupBy = 1350
         Filter = 1350
         Or = 1350
         Or = 1350
         Or = 1350
      End
   End
End
' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'VIEW',@level1name=N'detalle_lista_operarios3'
GO
EXEC sys.sp_addextendedproperty @name=N'MS_DiagramPaneCount', @value=1 , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'VIEW',@level1name=N'detalle_lista_operarios3'
GO
