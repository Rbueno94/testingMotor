USE [reingenieria]
GO
/****** Object:  Table [dbo].[auth_group]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[auth_group_permissions]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[auth_permission]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[auth_user]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[auth_user_groups]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[auth_user_user_permissions]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[django_admin_log]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[django_content_type]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[django_migrations]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[django_session]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[ESME_EM_Marcaciones]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[infolog]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_actividadcab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_actividaddet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_alertaresp]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_alertas]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_asigfiscalpuntoservicio]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_asigjefefiscal]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_asignacioncab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_asignaciondet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_asignaciondettemp]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_asignacionesdet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_asignacionesprocesadas]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_calendariocupo]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_cargo]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_cargoasignado]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_ciudad]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_cliente]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_cuporeal]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_cupoutilizado]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_dialibre]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_especializacion]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_feriados]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_generadoralertas]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_grupoempresarial]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_hisasigfiscalpuntoservicio]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_hisasigjefefiscal]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histactividadcab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histactividaddet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histasigfiscalpuntoservicio]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histasigjefefiscal]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histasignacioncab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histasignaciondet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histnotificacion]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histordenserviciocab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histordenserviciodet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histplanificacioncab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histplanificacionesp]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histplanificacionope]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histpuntoservicio]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histrelevamientocab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histrelevamientocupohoras]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histrelevamientodet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histrelevamientoesp]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_histrelevamientomensualeros]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_horariosoperario]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_horasnoprocesadas]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_horasprocesadas]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_motivos]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_nacionalidad]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_notificacion]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_operario]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_operario_profesion]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_operariosasignaciondet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_operariosordenesdet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_ordenserviciocab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_ordenserviciodet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_parametros]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_planificacioncab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_planificacionesp]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_planificacionope]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_procesosincronizacion]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_puntoservicio]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_relevamientocab]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_relevamientocupohoras]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_relevamientodet]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_relevamientoesp]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_relevamientomensualeros]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_remplazomanresp]    Script Date: 19/12/2019 16:24:16 ******/
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
/****** Object:  Table [dbo].[Operarios_remplazoscab]    Script Date: 19/12/2019 16:24:17 ******/
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
/****** Object:  Table [dbo].[Operarios_remplazosdet]    Script Date: 19/12/2019 16:24:17 ******/
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
/****** Object:  Table [dbo].[Operarios_sincronizacioncab]    Script Date: 19/12/2019 16:24:17 ******/
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
/****** Object:  Table [dbo].[Operarios_sincronizaciondet]    Script Date: 19/12/2019 16:24:17 ******/
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
/****** Object:  Table [dbo].[Operarios_tipohorario]    Script Date: 19/12/2019 16:24:17 ******/
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
/****** Object:  Table [dbo].[Operarios_tipoorden]    Script Date: 19/12/2019 16:24:17 ******/
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
/****** Object:  Table [dbo].[Operarios_tiposalario]    Script Date: 19/12/2019 16:24:17 ******/
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
/****** Object:  Table [dbo].[Operarios_tiposervicio]    Script Date: 19/12/2019 16:24:17 ******/
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
/****** Object:  Table [dbo].[Operarios_tiposervicioparticular]    Script Date: 19/12/2019 16:24:17 ******/
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
