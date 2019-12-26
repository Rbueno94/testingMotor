Performing system checks...

System check identified no issues (0 silenced).
SET DATEFORMAT ymd; SET DATEFIRST 7
()
SELECT SYSDATETIME()
()
SELECT TABLE_NAME, TABLE_TYPE FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = SCHEMA_NAME()
()
SELECT CAST(SERVERPROPERTY('ProductVersion') AS varchar)
()
SELECT [django_migrations].[app], [django_migrations].[name] FROM [django_migrations]
()
December 26, 2019 - 16:36:09
Django version 2.1.2, using settings 'reingenieria.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CTRL-BREAK.
username:GRUPOBAUDELET\5419069
passname:Elmejor2019
SET DATEFORMAT ymd; SET DATEFIRST 7
()
SELECT SYSDATETIME()
()
SELECT [auth_user].[id], [auth_user].[password], [auth_user].[last_login], [auth_user].[is_superuser], [auth_user].[username], [auth_user].[first_name], [auth_user].[last_name], [auth_user].[email], [auth_user].[is_staff], [auth_user].[is_active], [auth_user].[date_joined] FROM [auth_user] WHERE [auth_user].[username] = ?
('5419069',)
Cedula:Administrador
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Sucursal 50 - La plata
	Grupo:ADSyncAdmins
	Grupo:Users
	Grupo:Organization Management
	Grupo:gs_dirLaPlata
	Grupo:Propietarios del creador de directivas de grupo
	Grupo:Users
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de empresas
	Grupo:Users
	Grupo:Administradores de esquema
	Grupo:Users
	Grupo:IIS_IUSRS
	Grupo:Builtin
	Grupo:Administradores
	Grupo:Builtin
Mail:Administrador@grupobaudelet.com
Cedula:Invitado
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Invitados
	Grupo:Builtin
Mail:[]
Cedula:BAUDELETDC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Acceso compatible con versiones anteriores de Windows 2000
	Grupo:Builtin
	Grupo:Publicadores de certificados
	Grupo:Users
Mail:[]
Cedula:krbtgt
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Grupo de replicación de contraseña RODC denegada
	Grupo:Users
Mail:[]
Cedula:1463332
PrimerNombre:Victor Santiago
Segundo Nombre:Paniagua Ayala
title:GERENTE DE INFORMATICA
department:INFORMATICA
company:EL MEJOR - LA PLATA - PROACTIF
directReports:CN=Derlis Fidel Gomez Riveros,OU=DESVINCULADOS,DC=grupobaudelet,DC=com
Miembro de:
	Grupo:Grupo Baudelet
	Grupo:BPM - Grupo Baudelet
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
Mail:[]
Cedula:franck
PrimerNombre:Franck
Segundo Nombre:Baudelet
title:GERENTE GENERAL
department:DIRECCION
company:LA PLATA
directReports:[]
Miembro de:
	Grupo:Ssl vpn INFRA
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_dirSP
	Grupo:Avisos BPM LP
	Grupo:Gerencias - La Plata
	Grupo:La Plata
	Grupo:gs_gerenciaLP
	Grupo:gs_dirLaPlata
	Grupo:gs_dirEM
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de Hyper-V
	Grupo:Builtin
	Grupo:Administradores
	Grupo:Builtin
Mail:franck@laplata.com.py
Cedula:daniel
PrimerNombre:Daniel
Segundo Nombre:Baudelet
title:GERENTE GENERAL
department:DIRECCION
company:EL MEJOR
directReports:CN=Victor Paniagua,OU=DESVINCULADOS,DC=grupobaudelet,DC=com
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn INFRA
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Los especialistas - El Mejor
	Grupo:gs_dirSP
	Grupo:Licitaciones_EM
	Grupo:Grupo Impulsor EM
	Grupo:Ocasionales - EM
	Grupo:Informaciones - Web EM
	Grupo:Comercial - El Mejor
	Grupo:Gerencias - El Mejor
	Grupo:El Mejor
	Grupo:gs_dirLaPlata
	Grupo:gs_dirEM
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de empresas
	Grupo:Users
	Grupo:Administradores
	Grupo:Builtin
Mail:daniel@elmejor.com.py
Cedula:BAUDELETMAIL$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:$D31000-LQK28VESNV2A
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:SM_75922513b72943818
PrimerNombre:[]
Segundo Nombre:MSExchApproval 1f05a927-3be2-4fb9-aa03-b59fe3b56f4c
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:SystemMailbox{1f05a927-3028-4fbd-a09b-d60b18da0a94}@teconviene.com.py
Cedula:SM_851af416ea9b4e24a
PrimerNombre:[]
Segundo Nombre:SystemMailbox bb558c35-97f1-4cb9-8ff7-d53741dc928c
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:SystemMailbox{bb558c35-97f1-4cb9-8ff7-d53741dc928c}@teconviene.com.py
Cedula:SM_4eb4c785b9ab4be1b
PrimerNombre:[]
Segundo Nombre:MsExchDiscovery e0dc1c29-89c3-4034-b678-e6c29d823ed9
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:SystemMailbox{e0dc1c29-89c3-4034-b678-e6c29d823ed9}@teconviene.com.py
Cedula:SM_b48a14a7ce84432da
PrimerNombre:[]
Segundo Nombre:MsExchDiscoveryMailbox D919BA05-46A6-415f-80AD-7E09334BB852
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:DiscoverySearchMailbox{D919BA05-46A6-415f-80AD-7E09334BB852}@teconviene.com.py
Cedula:SM_aeb0d9e7edef40448
PrimerNombre:[]
Segundo Nombre:FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:FederatedEmail.4c1f4d8b-8179-4148-93bf-00a95fa1e042@teconviene.com.py
Cedula:SM_968df450b8c840fdb
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox89c82a74673844b5a03effde2a2a4ed5@grupobaudelet.com
Cedula:BAUDELETSQL2K8$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETSQL2K12$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETDC2$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Admins. del dominio
	Grupo:Users
Mail:[]
Cedula:BAUDELETSQL2K5$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETAV$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_sccm2012
	Grupo:Servidores RAS e IAS
	Grupo:Users
Mail:[]
Cedula:cesar.delvalle
PrimerNombre:Cesar
Segundo Nombre:Delvalle
title:DESARROLLADOR DE INFORMATICA
department:INFORMATICA
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
Mail:[]
Cedula:BAUDELETBSC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETSVY$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:794032
PrimerNombre:Lilian
Segundo Nombre:Guerrero
title:Relevador A
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:Lilian.Guerrero@elmejor.com.py
Cedula:cristina.navarro
PrimerNombre:Cristina
Segundo Nombre:Navarro
title:Jefe de Operaciones
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:coordinadoras
	Grupo:Grupo Impulsor EM
	Grupo:gs_CoorFisEM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:cristina.navarro@elmejor.com.py
Cedula:norma.amarilla
PrimerNombre:Norma
Segundo Nombre:Amarilla
title:Jefe de Operaciones
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:coordinadoras
	Grupo:Grupo Impulsor EM
	Grupo:gs_CoorFisEM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:norma.amarilla@elmejor.com.py
Cedula:1547583
PrimerNombre:Reinalda
Segundo Nombre:Lujan
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Reinalda.Lujan@elmejor.com.py
Cedula:1681406
PrimerNombre:Agustin
Segundo Nombre:Alvarenga
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Agustin.Alvarenga@elmejor.com.py
Cedula:1733194
PrimerNombre:Limpia
Segundo Nombre:Barboza
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:limpia.barboza@elmejor.com.py
Cedula:1923685
PrimerNombre:Mercedes
Segundo Nombre:Dominguez
title:Fiscal cubre Vacaciones
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:mercedes.dominguez@elmejor.com.py
Cedula:gladis.candia
PrimerNombre:Gladis
Segundo Nombre:Candia
title:Jefa de Capacitaciones Tecnicas
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:gs_CoorFisEM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Gladis.Candia@elmejor.com.py
Cedula:liza.meza
PrimerNombre:Liza
Segundo Nombre:Meza
title:Jefe de Operaciones
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:coordinadoras
	Grupo:Grupo Impulsor EM
	Grupo:gs_CoorFisEM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:liza.meza@elmejor.com.py
Cedula:2608527
PrimerNombre:Jorge
Segundo Nombre:Torales
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
Mail:[]
Cedula:3208526
PrimerNombre:Rosa
Segundo Nombre:Valdez
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Rosa.Valdez@elmejor.com.py
Cedula:3302571
PrimerNombre:Cristhian
Segundo Nombre:Sanabria
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Cristhian.Sanabria@elmejor.com.py
Cedula:3390828
PrimerNombre:Reinaldo
Segundo Nombre:Cortaza
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
Mail:reinaldo.cortaza@teconviene.com.py
Cedula:3437246
PrimerNombre:Virgilio
Segundo Nombre:Rodriguez
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Virgilio.Rodriguez@elmejor.com.py
Cedula:3528642
PrimerNombre:Rocio
Segundo Nombre:Villamayor
title:Relevador B
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:Rocio.Villamayor@elmejor.com.py
Cedula:mercedes.acosta
PrimerNombre:Mercedes
Segundo Nombre:Acosta
title:Jefe de Operaciones
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:coordinadoras
	Grupo:Grupo Impulsor EM
	Grupo:gs_CoorFisEM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:mercedes.acosta@elmejor.com.py
Cedula:3888374
PrimerNombre:Juana
Segundo Nombre:Sotelo
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:juana.sotelo@elmejor.com.py
Cedula:3849138
PrimerNombre:Ramon
Segundo Nombre:Galeano
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Ramon.Galeano@elmejor.com.py
Cedula:violeta.garcia
PrimerNombre:Violeta
Segundo Nombre:Garcia
title:Gerente Administrativo Financiero
department:ADMINSTRACIÓN
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Licitaciones_EM
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Informaciones - Web EM
	Grupo:Administracion - El Mejor
	Grupo:Gerencias - El Mejor
	Grupo:El Mejor
	Grupo:gs_gerAdministracionEM
	Grupo:gs_administracionEM
	Grupo:Invitados
	Grupo:Builtin
Mail:violeta.garcia@elmejor.com.py
Cedula:1898360
PrimerNombre:Hector
Segundo Nombre:Arana
title:Auxiliar Administrativo
department:ADMINISTRACION
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_administracionEM
Mail:Hector.Arana@elmejor.com.py
Cedula:3992917
PrimerNombre:Elsa
Segundo Nombre:Rios
title:Coordinadora de Calidad y Estandarización
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Calidad - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
	Grupo:gs_calidadEM
Mail:Elsa.Rios@elmejor.com.py
Cedula:577972
PrimerNombre:Claudia
Segundo Nombre:Bigorda
title:Ejecutivo Comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Comercial - El Mejor
	Grupo:gs_comercialEM
Mail:claudia.bigorda@elmejor.com.py
Cedula:608447
PrimerNombre:Gustavo
Segundo Nombre:Sosa
title:Ejecutivo Comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio con ST
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:gustavo.sosa@elmejor.com.py
Cedula:2288710
PrimerNombre:Mirian
Segundo Nombre:Cubilla
title:Jefa de Recursos Humanos
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:RRHH - El Mejor
	Grupo:El Mejor
	Grupo:gs_rrhhEM
	Grupo:gs_El_Mejor
Mail:mirian.cubilla@elmejor.com.py
Cedula:graciela.dietrich
PrimerNombre:Graciela
Segundo Nombre:Dietrich
title:Gerente de Operaciones y Gte. Gral Adjunta
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Licitaciones_EM
	Grupo:Comercial Ocasionales
	Grupo:coordinadoras
	Grupo:Grupo Impulsor EM
	Grupo:Informaciones - Web EM
	Grupo:Newsletter
	Grupo:Calidad - El Mejor
	Grupo:gs_marketingEM
	Grupo:Gerencias - El Mejor
	Grupo:El Mejor
	Grupo:gs_gerOperacionesEM
	Grupo:gs_gerComercialEM
	Grupo:gs_operacionesEM
	Grupo:gs_calidadEM
Mail:graciela.dietrich@elmejor.com.py
Cedula:4640608
PrimerNombre:Antonio
Segundo Nombre:Cristaldo
title:Jefe de Logística y Compras
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:antonio.cristaldo@elmejor.com.py
Cedula:fatima.paredes
PrimerNombre:Fatima
Segundo Nombre:Paredes
title:Gerente de Adm de RRHH
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
Mail:fatima.paredes@elmejor.com.py
Cedula:3550652
PrimerNombre:Emiliano
Segundo Nombre:Gomez
title:CAPACITADOR TECNICO
department:DO
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Emiliano.Gomez@elmejor.com.py
Cedula:2467049
PrimerNombre:Antonio
Segundo Nombre:Montania
title:Supervisor de Salud y Seguridad Ocupacional
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:SSO RRHH -El Mejor
	Grupo:SSO RRHH - El Mejor
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_operacionesEM
	Grupo:gs_rrhhEM
Mail:Antonio.Montania@elmejor.com.py
Cedula:maria.apodaca
PrimerNombre:Maria
Segundo Nombre:Apodaca
title:Coordinadora de Reclutamiento y Selección
department:GT
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:gs_gestiontalentoEM
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Gestion de Talento
	Grupo:El Mejor
	Grupo:gs_doEM
	Grupo:gs_El_Mejor
	Grupo:Invitados
	Grupo:Builtin
Mail:maria.apodaca@elmejor.com.py
Cedula:3518163
PrimerNombre:Guillermo
Segundo Nombre:Casañas
title:Ejecutivo Comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:guillermo.casanas@teconviene.com.py
Cedula:1877012
PrimerNombre:Paulo
Segundo Nombre:Gonzalez
title:Ejecutivo Comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:Paulo.Gonzalez@elmejor.com.py
Cedula:rosario.cabrera
PrimerNombre:Rosario
Segundo Nombre:Cabrera
title:Gerente Comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Licitaciones_EM
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Comercial - El Mejor
	Grupo:Gerencias - El Mejor
	Grupo:El Mejor
	Grupo:gs_gerComercialEM
	Grupo:gs_comercialEM
	Grupo:Invitados
	Grupo:Builtin
Mail:rosario.cabrera@elmejor.com.py
Cedula:BAUDELETGEN$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3962032
PrimerNombre:Mariza
Segundo Nombre:Caceres
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:Mariza.Caceres@elmejor.com.py
Cedula:4344696
PrimerNombre:Jesus
Segundo Nombre:Leon
title:AUXILIAR CONTABLE
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_administracionEM
Mail:[]
Cedula:spam
PrimerNombre:Spam
Segundo Nombre:Baudelet
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:spam@grupobaudelet.com
Cedula:SQLServicesUser
PrimerNombre:[]
Segundo Nombre:SQLServicesUser
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETBACKUP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:elva.gomez
PrimerNombre:Elva Maria
Segundo Nombre:Gomez Chavez
title:Gerencia Administrativa
department:Administracion
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Seleccion La Plata
	Grupo:Avisos BPM LP
	Grupo:Administracion - La Plata
	Grupo:Gerencias - La Plata
	Grupo:gs_gerAdministracionLP
	Grupo:La Plata
	Grupo:gs_gerenciaLP
	Grupo:gs_AdministracionLP
Mail:elva.gomez@laplata.com.py
Cedula:elizabeth.gonzalez
PrimerNombre:Elizabeth
Segundo Nombre:Gonzalez de Baudelet
title:Gerencia de Auditoria
department:Auditoria
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:Gerencias - La Plata
	Grupo:gs_gerAuditoriaLP
	Grupo:La Plata
	Grupo:gs_gerenciaLP
	Grupo:gs_dirLaPlata
Mail:elizabeth.gonzalez@laplata.com.py
Cedula:rodrigo.alvarez
PrimerNombre:Juan Rodrigo
Segundo Nombre:Alvarez Rabito
title:Gerente
department:Desarrollo Comercial
company:La Plata
directReports:['CN=Gabriela Elizabeth Lugo Romero,OU=Marketing,OU=La Plata,OU=GrupoBaudelet,DC=grupobaudelet,DC=com', 'CN=Elson Mohamed Portelli Velazquez,OU=Marketing,OU=La Plata,OU=GrupoBaudelet,DC=grupobaudelet,DC=com', 'CN=Miguel Angel Ramirez Portillo,OU=DESVINCULADOS,DC=grupobaudelet,DC=com', 'CN=Cynthia Maria Teresita Mendez Garcete,OU=DESVINCULADOS,DC=grupobaudelet,DC=com', 'CN=Alberto Javier Quintana Berdejo,OU=Desarrollo-Comercial,OU=La Plata,OU=GrupoBaudelet,DC=grupobaudelet,DC=com']
Miembro de:
	Grupo:gs_comercialLP
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_informaticaLP
	Grupo:Marketing - La Plata
	Grupo:Informatica - La Plata
	Grupo:Seleccion La Plata
	Grupo:Avisos BPM LP
	Grupo:Gerencias - La Plata
	Grupo:Comercial - La Plata
	Grupo:gs_gerComercialLP
	Grupo:gs_gerMarketingLP
	Grupo:La Plata
	Grupo:gs_gerenciaLP
	Grupo:Administradores
	Grupo:Builtin
Mail:rodrigo.alvarez@laplata.com.py
Cedula:4293378
PrimerNombre:Diego Manuel
Segundo Nombre:Mendoza Posteley
title:Auditoria
department:Auditoria
company:La Plata
directReports:[]
Miembro de:
Mail:diego.mendoza@teconviene.com.py
Cedula:4224915
PrimerNombre:Almi Raquel
Segundo Nombre:Encina Talavera
title:Administración
department:Administracion
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:Administracion - La Plata
	Grupo:La Plata
	Grupo:gs_AdministracionLP
Mail:almi.encina@laplata.com.py
Cedula:2012534
PrimerNombre:Juan Salvador
Segundo Nombre:Aquino
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc00
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:juan.aquino@laplata.com.py
Cedula:2119761
PrimerNombre:Mariano
Segundo Nombre:Montania Monges
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc00
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:mariano.montania@laplata.com.py
Cedula:3439301
PrimerNombre:Daniel
Segundo Nombre:Ramos Godoy
title:Jefe Operativo
department:Desarrollo Comercial
company:La Plata
directReports:[]
Miembro de:
	Grupo:gs_comercialLP
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Seleccion La Plata
	Grupo:Avisos BPM LP
	Grupo:Comercial - La Plata
	Grupo:La Plata
	Grupo:gs_asesoresLP
Mail:daniel.ramos@laplata.com.py
Cedula:3640380
PrimerNombre:Carlos Antonio
Segundo Nombre:Amadit Ferreira
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc27
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:carlos.amadit@laplata.com.py
Cedula:3663093
PrimerNombre:Luciano Fernando
Segundo Nombre:Meza Ferreira
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc06
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:luciano.meza@laplata.com.py
Cedula:3446465
PrimerNombre:Carlos Gabriel
Segundo Nombre:Ortiz Samaniego
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc08
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:carlos.ortiz@laplata.com.py
Cedula:3496649
PrimerNombre:Diego Fernando
Segundo Nombre:Mendieta Miranda
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc09
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:diego.mendieta@laplata.com.py
Cedula:2037109
PrimerNombre:Osvaldo Gabriel
Segundo Nombre:Mendez Benitez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc23
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:osvaldo.mendez@laplata.com.py
Cedula:4651403
PrimerNombre:Cristhian Manuel
Segundo Nombre:Gonzalez
title:Asesor Comercial
department:Comercial
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_asesorZona3LP
	Grupo:Avisos BPM LP
	Grupo:Supervisores - La Plata
	Grupo:La Plata
	Grupo:gs_asesoresLP
Mail:cristhian.gonzalez@laplata.com.py
Cedula:2223020
PrimerNombre:David Alfredo
Segundo Nombre:Rojas Mancia
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc20
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:david.rojas@laplata.com.py
Cedula:4181397
PrimerNombre:Ernesto Damian
Segundo Nombre:Aguero Dure
title:Asesor Comercial
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_asesorZona4LP
	Grupo:Avisos BPM LP
	Grupo:Supervisores - La Plata
	Grupo:La Plata
	Grupo:gs_asesoresLP
Mail:ernesto.aguero@laplata.com.py
Cedula:2489871
PrimerNombre:Derlis Ismael
Segundo Nombre:Saldivar Ferreira
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc25
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:derlis.saldivar@laplata.com.py
Cedula:1665673
PrimerNombre:Cesar Tadeo
Segundo Nombre:Rojas Coronel
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc02
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:cesar.rojas@laplata.com.py
Cedula:3219639
PrimerNombre:Marcio Dejesus
Segundo Nombre:Rodriguez Machuca
title:Encargado CC
department:Contact Center
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Internet intermedio con RS
	Grupo:Ssl vpn LP
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center - La Plata
	Grupo:gs_contactLP_Encargado
	Grupo:Avisos BPM LP
	Grupo:gs_contactLP
	Grupo:La Plata
Mail:marcio.rodriguez@laplata.com.py
Cedula:3796161
PrimerNombre:Ruben Dario
Segundo Nombre:Gimenez Olmedo
title:Encargado Suc. 18
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc18
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:ruben.gimenez@laplata.com.py
Cedula:3786235
PrimerNombre:Alberto Milciades
Segundo Nombre:Morel Marín
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc04
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:alberto.morel@laplata.com.py
Cedula:4333000
PrimerNombre:Edgar Eduardo
Segundo Nombre:Cabañas Espinoza
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc26
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:edgar.cabanas@laplata.com.py
Cedula:5032664
PrimerNombre:Pablo Daniel
Segundo Nombre:Dure Orrego
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc22
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:pablo.dure@laplata.com.py
Cedula:feliciano.melgarejo
PrimerNombre:Feliciano
Segundo Nombre:Melgarejo Mendez
title:Gerente
department:Auditoria
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_auditoriaLP
	Grupo:gs_gerenciaLP
Mail:feliciano.melgarejo@laplata.com.py
Cedula:3984047
PrimerNombre:Ricardo Javier
Segundo Nombre:Sanchez Aguilar
title:Asesor Comercial
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_asesorZona1
	Grupo:Avisos BPM LP
	Grupo:Supervisores - La Plata
	Grupo:La Plata
	Grupo:gs_asesoresLP
Mail:ricardo.sanchez@laplata.com.py
Cedula:LPSUCOM01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3216232
PrimerNombre:Francisco
Segundo Nombre:Ozuna Gimenez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc28
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:francisco.ozuna@laplata.com.py
Cedula:LP23SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:seguridadIT
PrimerNombre:Seguridad
Segundo Nombre:IT
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:IIS_IUSRS
	Grupo:Builtin
Mail:seguridadIT@grupobaudelet.com
Cedula:patricia
PrimerNombre:Patricia
Segundo Nombre:Baudelet
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:patricia@elmejor.com.py
Cedula:3980304
PrimerNombre:Mathias
Segundo Nombre:Baudelet
title:Jefe de la Unidad de Servicios Especializados
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Ssl vpn INFRA
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:mathias@elmejor.com.py
Cedula:patricia.benitez
PrimerNombre:Patricia Laura
Segundo Nombre:Benitez
title:Jefe de Contact Center
department:Contact Center
company:El Mejor
directReports:CN=Karina Nathalia Meza Carrera,OU=CONTACT,OU=El Mejor,OU=GrupoBaudelet,DC=grupobaudelet,DC=com
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:gs_supCC
	Grupo:Contact Center
	Grupo:gs_contactEM
	Grupo:gs_callEM
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:patricia.benitez@elmejor.com.py
Cedula:1911429
PrimerNombre:Benita Estanislaa
Segundo Nombre:Orrego Martinez
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:benita.orrego@elmejor.com.py
Cedula:BAUDELETALI$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:perla.medina
PrimerNombre:Perla Isolina
Segundo Nombre:Medina Lavand
title:ADM Y FINANZAS
department:Administracion
company:Proactif
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Gerencias - Proactif
	Grupo:gs_gerAdministracionPC
	Grupo:gs_administracionPC
Mail:perla.medina@proactif.com.py
Cedula:PCOPE02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_proactifPCs
Mail:[]
Cedula:PCVEN01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_proactifPCs
Mail:[]
Cedula:SM_0055f3de7c174a8a8
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxd955210b16384c63ba7a250a19e548b1@grupobaudelet.com
Cedula:franck.proactif
PrimerNombre:Franck
Segundo Nombre:Baudelet Proactif
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:franck.baudelet@proactif.com.py
Cedula:daniel.proactif
PrimerNombre:Daniel
Segundo Nombre:Baudelet Proactif
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:daniel.baudelet@proactif.com.py
Cedula:1627280
PrimerNombre:Gladys Zunilda
Segundo Nombre:Fernandez Mancuello
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:gladys.fernandez@elmejor.com.py
Cedula:patricia.elmejor
PrimerNombre:Patricia
Segundo Nombre:Benitez El Mejor
title:CONTACT CENTER
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
Mail:[]
Cedula:3652012
PrimerNombre:Juan Antonio
Segundo Nombre:Flor Vega
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc19
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:juan.flor@laplata.com.py
Cedula:BAUDELETSCCM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Admins. del dominio
	Grupo:Users
Mail:[]
Cedula:2942114
PrimerNombre:Laura
Segundo Nombre:Maqueda de Bogarin
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:laura.maqueda@elmejor.com.py
Cedula:PCLOG04$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_proactifPCs
Mail:[]
Cedula:1328195
PrimerNombre:Luz Wilma
Segundo Nombre:Benitez
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:luz.benitez@elmejor.com.py
Cedula:david.hermosa
PrimerNombre:David Ariel
Segundo Nombre:Hermosa Pereira
title:Coordinador de Sistemas
department:Tecnologías de la Información y Comunicación
company:El Mejor S.R.L.
directReports:[]
Miembro de:
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_gerTecnologiaEM
	Grupo:GTIC
	Grupo:Informatica - El Mejor
	Grupo:BPM - Grupo Baudelet
	Grupo:Informatica
	Grupo:El Mejor
	Grupo:gs_El_Mejor
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:david.hermosa@elmejor.com.py
Cedula:BAUDELETBPM-DES$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETCORREO$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:SM_c1b1ffbe0c2241079
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxe39b00cfb1d94f2e881532c28af21636@grupobaudelet.com
Cedula:SM_21a4d5acce134dea8
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox7954ffac217344b3a4c35a370e54a685@grupobaudelet.com
Cedula:SM_e262e197d7df45788
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox48b5da122158416087c03f392ed20b6b@grupobaudelet.com
Cedula:SM_0550dd737d20497bb
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox8641d8ba4dbc46c28efb35b0739b9e32@grupobaudelet.com
Cedula:SM_ddeecd72acc94492b
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox677be2e80d154647bba75eacfb723d17@grupobaudelet.com
Cedula:3884955
PrimerNombre:Irma
Segundo Nombre:Rodriguez
title:Jefa de Operaciones
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:gs_CoorFisEM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:irma.rodriguez@elmejor.com.py
Cedula:patricia.pereira
PrimerNombre:Patricia
Segundo Nombre:Pereira Ferreira
title:Jefa
department:Informática
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Monitoreo
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_informaticaLP
	Grupo:Informatica - La Plata
	Grupo:Seleccion La Plata
	Grupo:Avisos BPM LP
	Grupo:BPM - Grupo Baudelet
	Grupo:La Plata
	Grupo:Informatica
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de empresas
	Grupo:Users
	Grupo:Administradores
	Grupo:Builtin
Mail:patricia.pereira@laplata.com.py
Cedula:BAUDELETTESTBPM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETIIS$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP15SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETBIZ$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:ruben.f
PrimerNombre:Ruben Dario
Segundo Nombre:Foj
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:ruben.f@spartanchemical.com.ar
Cedula:12279119
PrimerNombre:Jorge Osvaldo
Segundo Nombre:Vela
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
Mail:jorge.vela@spartanargentina.com
Cedula:907776306
PrimerNombre:Juana
Segundo Nombre:Herrera
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:juana.herrera@spartanargentina.com
Cedula:franck.spartan
PrimerNombre:Franck
Segundo Nombre:Baudelet Spartan
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_dirSP
	Grupo:Gerencia Spartan
Mail:franck@spartanchemical.com.ar
Cedula:daniel.spartan
PrimerNombre:Daniel
Segundo Nombre:Baudelet Spartan
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_dirSP
	Grupo:Gerencia Spartan
Mail:daniel@spartanchemical.com.ar
Cedula:karina.p
PrimerNombre:Karina
Segundo Nombre:Pirraglia
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Informaciones Web - SA
	Grupo:Administracion -Spartan Argentina
Mail:karina.p@spartanchemical.com.ar
Cedula:28121574
PrimerNombre:Hernán Jesus
Segundo Nombre:Castano
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:hernan.castano@spartanargentina.com
Cedula:BAUDELETDES-BPM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETFTP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCALI02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:SM_43057d23901a48c3b
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox5380f46e04ff4221beefbb8feb9c924e@grupobaudelet.com
Cedula:SM_2416b70349104b1c8
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox971c595a09ba4126ab12694f3f375745@grupobaudelet.com
Cedula:SM_e38b3e3916bf44e39
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox77e89f6b11ac45c68e541e8016f80c1d@grupobaudelet.com
Cedula:SM_b03d24fde69d4fbeb
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxd2bd162f60254644987aead8d4460a3d@grupobaudelet.com
Cedula:SM_ba0b3a57180d41f78
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox94abeb339a1244c2a1e6c68a8b94d71f@grupobaudelet.com
Cedula:SM_9a29e2f7723a4173a
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox3e8676d8e8ee4546beaed91767330b94@grupobaudelet.com
Cedula:BAUDELETSHARE$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:lisiane.mc
PrimerNombre:Lisiane
Segundo Nombre:Marques Correa
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Informaciones Web - SA
Mail:lisiane.mc@spartanchemical.com.ar
Cedula:1043425
PrimerNombre:Blanca Isabel
Segundo Nombre:Gonzalez Leon
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:blanca.gonzalez@elmejor.com.py
Cedula:LP06SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCOMER03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_proactifPCs
Mail:[]
Cedula:BAUDELETBPMDESA$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4073782
PrimerNombre:Derlis Fidel
Segundo Nombre:Gomez Riveros
title:HELPDESK INFORMATICA
department:INFORMATICA
company:EL MEJOR S.R.L.
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
Mail:[]
Cedula:BAUDELETBPMDEV$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:28463772
PrimerNombre:Martin Angel
Segundo Nombre:Pirraglia
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:martin.pirraglia@spartanargentina.com
Cedula:30963587
PrimerNombre:Marisol Cintia
Segundo Nombre:Gerry
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:marisol.gerry@spartanargentina.com
Cedula:30131892
PrimerNombre:Ezequiel Alejandro
Segundo Nombre:Ragone
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:ezequiel.ragone@spartanargentina.com
Cedula:12226720
PrimerNombre:Sergio
Segundo Nombre:Barroso
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:sergio.barroso@spartanargentina.com
Cedula:SM_3da4d0d8a32240559
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox3f9b364c471d4e64be70d17930b593ab@grupobaudelet.com
Cedula:PCADM03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_proactifPCs
Mail:[]
Cedula:spartan.web
PrimerNombre:Spartan
Segundo Nombre:Web
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:spartan.web@spartanchemical.com.ar
Cedula:2475718
PrimerNombre:Ramon
Segundo Nombre:Franco Olmedo
title:Cobrador
department:ADM
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_administracionEM
Mail:ramon.franco@elmejor.com.py
Cedula:25316465
PrimerNombre:Gabriel
Segundo Nombre:Viñas
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:gabriel.vinas@spartanargentina.com
Cedula:$DUPLICATE-a2d
PrimerNombre:Gabriel
Segundo Nombre:Viñas
title:Ejecutivo Comercial
department:Comercial
company:Spartan Argentina
directReports:[]
Miembro de:
Mail:[]
Cedula:2967925
PrimerNombre:Edgar Antonio
Segundo Nombre:Martinez Caceres
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:edgar.martinez@elmejor.com.py
Cedula:LP14SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCAP03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3415522
PrimerNombre:Osmar
Segundo Nombre:Lopez
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:osmar.lopez@elmejor.com.py
Cedula:EMCOMER011$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP22SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3379767
PrimerNombre:Isabelina
Segundo Nombre:Canete Aquino
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
	Grupo:gs_dirEM
Mail:isabelina.canete@elmejor.com.py
Cedula:1970213
PrimerNombre:Mirian
Segundo Nombre:Aguero
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:mirian.aguero@elmejor.com.py
Cedula:LP10SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3479550
PrimerNombre:Guillermo
Segundo Nombre:Britez
title:Ejecutivo de Ventas Ocasionales
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
Mail:[]
Cedula:4976896
PrimerNombre:Diego Daniel
Segundo Nombre:Figueredo González
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc07
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:diego.figueredo@laplata.com.py
Cedula:BAUDELETRODC1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:krbtgt_35807
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETSQL2005$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELET2K14$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPFB01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCWA02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3632895
PrimerNombre:Raul Alberto
Segundo Nombre:Amarilla Portillo
title:Servicio Técnico - Proactif
department:Servicio Tecnico
company:Proactif
directReports:[]
Miembro de:
	Grupo:Internet intermedio con ST
	Grupo:Proactif Care
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
Mail:raul.amarilla@proactif.com.py
Cedula:BAUDELETRDP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMRRHH12$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCLOG10$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMIT02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:andres.suarez
PrimerNombre:Andres Adolfo
Segundo Nombre:Suarez Carrillo
title:Gerente General
department:Gerencia General
company:Proactif
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Gerencias - Proactif
	Grupo:gs_gerenciaPC
Mail:andres.suarez@proactif.com.py
Cedula:BAUDELETBSCW$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP25SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOMER002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCONTACT01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:20406736
PrimerNombre:Guillermo
Segundo Nombre:Arana
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:gs_invitados
	Grupo:El Mejor
Mail:arana@corporater.com
Cedula:patricia.spartan
PrimerNombre:Patricia
Segundo Nombre:Benitez Spartan
title:CONTACT CENTER
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
Mail:cobranzas@grupobaudelet.com
Cedula:comunicaciones
PrimerNombre:comunicaciones
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:comunicaciones@elmejor.com.py
Cedula:LP29SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3783191
PrimerNombre:Walter
Segundo Nombre:Velazquez Colman
title:Encargado Suc. 34
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc34
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:walter.velazquez@laplata.com.py
Cedula:LP17SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP13SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETWSVY$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3382591
PrimerNombre:Alexis Daniel
Segundo Nombre:Arzamendia Ruiz
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc14
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:alexis.arzamendia@laplata.com.py
Cedula:3798927
PrimerNombre:Guillermo Ramon
Segundo Nombre:Trulls Vazquez
title:Enc. Compras y Logistica
department:Logistica
company:Proactif
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:gs_logisticaPC
Mail:guillermo.trulls@proactif.com.py
Cedula:4198458
PrimerNombre:Jorge Ariel
Segundo Nombre:Duarte Marin
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc11
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:jorge.duarte@laplata.com.py
Cedula:4222393
PrimerNombre:Diosnel
Segundo Nombre:Ocampos Lopez
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:coordinadoras
	Grupo:Grupo Impulsor EM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:diosnel.ocampos@elmejor.com.py
Cedula:mathias.baudelet
PrimerNombre:Mathias Arthur
Segundo Nombre:Baudelet Davalos
title:Compras y Relaciones Internacionales
department:Administracion
company:Proactif
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_gerAdministracionPC
	Grupo:gs_administracionPC
Mail:mathias.baudelet@proactif.com.py
Cedula:3562648
PrimerNombre:Alba Rossana
Segundo Nombre:Rolon Correa
title:Auxiliar Administrativo
department:ADMINISTRACION
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:El Mejor
	Grupo:gs_administracionEM
	Grupo:Invitados
	Grupo:Builtin
Mail:alba.rolon@elmejor.com.py
Cedula:4805906
PrimerNombre:Diego Andres
Segundo Nombre:Re Giménez
title:Analista de Procesos
department:Informatica
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Monitoreo
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Informatica - Proactif Care
	Grupo:gs_invitados
	Grupo:BPM - Grupo Baudelet
	Grupo:Informatica
	Grupo:gs_it
Mail:diego.re@proactif.com.py
Cedula:5334220
PrimerNombre:Luciana Paula
Segundo Nombre:Jimenez
title:Coordinadora de Contratos, Cobros
department:ADMINISTRACION
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Administracion - El Mejor
	Grupo:El Mejor
	Grupo:gs_administracionEM
	Grupo:Invitados
	Grupo:Builtin
Mail:luciana.jimenez@elmejor.com.py
Cedula:BAUDELETSQLNAV$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3999731
PrimerNombre:Christian Antonio
Segundo Nombre:Alvarenga Salinas
title:Desarrollador
department:Informatica
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_informaticaLP
	Grupo:Informatica - La Plata
	Grupo:Avisos BPM LP
	Grupo:BPM - Grupo Baudelet
	Grupo:La Plata
	Grupo:Informatica
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:christian.alvarenga@laplata.com.py
Cedula:2020070
PrimerNombre:Paulo Christian
Segundo Nombre:Carvallo Duarte
title:Ejecutivo de Ventas Ocasionales
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
Mail:[]
Cedula:3884127
PrimerNombre:Anahy Belen
Segundo Nombre:Benegas Candia
title:Asistente Social
department:GT
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Invitados
	Grupo:Builtin
Mail:anahy.benegas@elmejor.com.py
Cedula:4420881
PrimerNombre:Sofia
Segundo Nombre:Gomez
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center
	Grupo:gs_contactEM
	Grupo:gs_callEM
	Grupo:El Mejor
Mail:sofia.gomez@elmejor.com.py
Cedula:2023066
PrimerNombre:Lourdes
Segundo Nombre:Garcia de Arguello
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
Mail:lourdes.garcia@teconviene.com.py
Cedula:BAUDELETKAS$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5336115
PrimerNombre:Oscar Javier
Segundo Nombre:Martinez Alvarez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc33
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:oscar.martinez@laplata.com.py
Cedula:LP31SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:2179780
PrimerNombre:Monica Elizabeth
Segundo Nombre:Rodriguez Rolon
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:Administracion - La Plata
	Grupo:La Plata
	Grupo:gs_AdministracionLP
Mail:monica.rodriguez@laplata.com.py
Cedula:1111124
PrimerNombre:Martin Dario
Segundo Nombre:Gimenez Almeida
title:Jefe Comercial PC
department:Comercial
company:[]
directReports:[]
Miembro de:
	Grupo:Internet intermedio con RS
	Grupo:Ssl vpn PC
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:martin.gimenez@proactif.com.py
Cedula:EMADM006$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDEBPMTEST$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOMER008$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4405666
PrimerNombre:Diego Alcides
Segundo Nombre:Sanchez Ayala
title:Logistica
department:Logistica
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Logistica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_logisticaLP
Mail:diego.sanchez@laplata.com.py
Cedula:4006282
PrimerNombre:Juan Rodrigo
Segundo Nombre:Peralta Villalba
title:Cobrador Proactif Care
department:Administracion PC
company:Proactif Care S.A.
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:rodrigo.peralta@proactif.com.py
Cedula:EMIMP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5511678
PrimerNombre:Hugo Javier
Segundo Nombre:Ojeda
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc24
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:hugo.ojeda@laplata.com.py
Cedula:INFO06-PC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMDO081$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP01SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:soporte.evoxys
PrimerNombre:soporte.evoxys
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:gs_invitados
Mail:[]
Cedula:4660201
PrimerNombre:ROSA ISABEL
Segundo Nombre:RODAS MARTINEZ
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_comercialPC
Mail:rosa.rodas@proactif.com.py
Cedula:LPSUCALL01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETAPP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETRDC2$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:evoxys.soporte
PrimerNombre:Evoxys
Segundo Nombre:Soporte
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Ssl vpn PROV
	Grupo:GrupoBaudelet
	Grupo:gs_invitados
Mail:[]
Cedula:6629607
PrimerNombre:Yessica Rosana
Segundo Nombre:Lopez Ramirez
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
Mail:[]
Cedula:5358744
PrimerNombre:Alberto Javier
Segundo Nombre:Quintana Berdejo
title:Encargado de Marketing
department:Desarrollo Comercial
company:La Plata
directReports:[]
Miembro de:
Mail:alberto.quintana@laplata.com.py
Cedula:carolina.vega
PrimerNombre:Carolina
Segundo Nombre:Vega
title:Auxiliar de Provisión
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:RRHH - El Mejor
	Grupo:El Mejor
	Grupo:gs_rrhhEM
Mail:carolina.vega@elmejor.com.py
Cedula:LPAUDIT01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3531598
PrimerNombre:Laura
Segundo Nombre:Benitez Cardozo
title:Ejecutiva de Cuentas
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
	Grupo:gs_El_Mejor
Mail:laura.benitez@elmejor.com.py
Cedula:4894670
PrimerNombre:Patricia Maria
Segundo Nombre:Báez Gonzalez
title:Auxiliar Administrativo
department:ADMINISTRACION
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Administracion - El Mejor
	Grupo:El Mejor
	Grupo:gs_administracionEM
Mail:patricia.baez@elmejor.com.py
Cedula:5024922
PrimerNombre:Liz Andrea
Segundo Nombre:Gibbons Cabrera
title:Auxiliar de Legales
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_rrhhEM
Mail:liz.gibbons@elmejor.com.py
Cedula:EMOPE009$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMMARK$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGERADM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGEROPE$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:evoxys.remoto
PrimerNombre:Evoxys
Segundo Nombre:Remoto
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Ssl vpn PROV
	Grupo:GrupoBaudelet
	Grupo:gs_invitados
Mail:[]
Cedula:5642589
PrimerNombre:Nancy Rocio
Segundo Nombre:Gonzalez
title:OPERADORA CONTACT CENTER
department:CONTACT CENTER
company:[]
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_contactPC
	Grupo:gs_comercialPC
Mail:nancy.gonzalez@proactif.com.py
Cedula:osvaldo.pedrozo
PrimerNombre:Osvaldo Ariel
Segundo Nombre:Pedrozo Saist
title:Auxiliar Informatico
department:Informatica
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Soporte TIC LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_informaticaLP
	Grupo:Informatica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:Informatica
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:osvaldo.pedrozo@laplata.com.py
Cedula:4581302
PrimerNombre:Juan Gabriel
Segundo Nombre:Fernandez Martinez
title:Vendedor de Salon
department:Comercial
company:[]
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_comercialPC
Mail:juan.fernandez@proactif.com.py
Cedula:EMCCSUP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGERGT$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMRRHH004$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGERCOMER$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOMER003$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPSUCALL07$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCOM02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOCA01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP33SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOMER010$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:2121732
PrimerNombre:Luz Diana
Segundo Nombre:Palacios Morel
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center
	Grupo:gs_contactEM
	Grupo:gs_callEM
	Grupo:El Mejor
Mail:luz.palacios@elmejor.com.py
Cedula:EMCOMER005$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPADM05$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE023$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE014$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE011$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE024$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCAP3$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPAUD01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE008$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE012$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOORD003$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCAL001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOORD004$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOORD001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE005$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCAP1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMADM004$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGT002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE007$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCAP2$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMASISD01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE010$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMADM001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMRRHH005$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGT005$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMJEFCC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOMER009$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP24SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE022$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOMER007$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMRRHH001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMRRHH002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMRRHH003$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMADM002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMADM003$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCC003$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCC002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE025$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOORD002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE021$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMDEP03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP40SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE020$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE017$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LIBRE$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGT001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4971534
PrimerNombre:Pedro Antonio
Segundo Nombre:Sosa Zaracho
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc15
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:pedro.sosa@laplata.com.py
Cedula:PCCONTACT02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE018$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCASISL01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGT004$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPLOG01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCOME02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCONTACT03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3951417
PrimerNombre:Luis Alberto
Segundo Nombre:Ovelar Rodriguez
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_comercialPC
Mail:luis.ovelar@proactif.com.py
Cedula:PCCOM01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOMER001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5478640
PrimerNombre:Diana Pamela
Segundo Nombre:Aricaye Chamorro
title:OPERADORA CONTACT CENTER
department:Contact Center
company:[]
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
	Grupo:gs_contactPC
Mail:diana.aricaye@proactif.com.py
Cedula:4135403
PrimerNombre:Melissa
Segundo Nombre:Baudelet Davalos
title:AUXILIAR DE GESTION
department:DO
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:melissa.baudelet@elmejor.com.py
Cedula:LPOPE01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:susana.cabañas
PrimerNombre:Susana Haidee
Segundo Nombre:Cabañas de Gonzalez
title:Coodinadora Contable
department:ADMINISTRACION
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio con ST
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Administracion - El Mejor
	Grupo:El Mejor
	Grupo:gs_administracionEM
Mail:susana.cabanas@elmejor.com.py
Cedula:PCSHR2$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPOPE02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMADM005$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE016$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMDB01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP41SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:innovaciones
PrimerNombre:innovaciones
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
Mail:innovaciones@elmejor.com.py
Cedula:EMOPE015$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4598046
PrimerNombre:Claudia
Segundo Nombre:Ortiz
title:Capacitadora
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:claudia.ortiz@elmejor.com.py
Cedula:EMCOMER006$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:2920507
PrimerNombre:Wilfrido
Segundo Nombre:Benitez Baez
title:Logistica
department:Logistica
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Logistica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_logisticaLP
Mail:wilfrido.benitez@laplata.com.py
Cedula:bizagi_mail
PrimerNombre:Bizagi Mail
Segundo Nombre:BPM
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores
	Grupo:Builtin
Mail:bizagi.mail@grupobaudelet.com
Cedula:4667537
PrimerNombre:Luis Javier
Segundo Nombre:Fretes Quiñonez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc41
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:luis.fretes@laplata.com.py
Cedula:balticlp.export
PrimerNombre:BalticLP
Segundo Nombre:Exportacion
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:balticem.export
PrimerNombre:BalticEM
Segundo Nombre:Exportacion
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPADM02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCOME03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPOPE03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMSALTOS$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGT003$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP42SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:maria.orzusa
PrimerNombre:Maria Emilia
Segundo Nombre:Orzusa Viveros
title:Auxiliar de Selección
department:GT
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:gs_gestiontalentoEM
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Gestion de Talento
	Grupo:El Mejor
	Grupo:gs_doEM
Mail:maria.orzusa@elmejor.com.py
Cedula:1580925
PrimerNombre:Amalia
Segundo Nombre:Caceres Roman
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:amalia.caceres@elmejor.com.py
Cedula:BAUDELETINFO$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP35SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:2198114
PrimerNombre:Liz Natalia
Segundo Nombre:Rojas
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:liz.rojas@elmejor.com.py
Cedula:EMCOMER004$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3170438
PrimerNombre:Natalia
Segundo Nombre:Amarilla Montanez
title:Ejecutivo Comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE003$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4696797
PrimerNombre:Pamela Inés Juliana
Segundo Nombre:Sánchez Ortiz
title:Representante de Atención al Cliente
department:GT
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:gs_gestiontalentoEM
	Grupo:Grupo Baudelet
	Grupo:Gestion de Talento
	Grupo:El Mejor
	Grupo:gs_doEM
Mail:pamela.sanchez@elmejor.com.py
Cedula:5030785
PrimerNombre:Derlis Cesar
Segundo Nombre:Benitez Nuñez
title:Asistente Administrativo
department:Administracion Proactif
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:gs_administracionPC
Mail:derlis.benitez@proactif.com.py
Cedula:PCLIBRE$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:1527878
PrimerNombre:WALBERTO FRANCISCO
Segundo Nombre:PALACIOS CACERES
title:Asesor Comercial
department:Comercial Proactif
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_comercialPC
Mail:walberto.palacios@proactif.com.py
Cedula:LPCOM02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETTMGII$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5389188
PrimerNombre:Wilson Gabriel
Segundo Nombre:Baez Lopez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc32
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:wilson.baez@laplata.com.py
Cedula:rocio.franco
PrimerNombre:Rocio
Segundo Nombre:Franco Ortega
title:Gerente de Gestión de Talento
department:GT
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Informaciones - Web EM
	Grupo:Etica - El Mejor
	Grupo:Gestion de Talento
	Grupo:Gerencias - El Mejor
	Grupo:El Mejor
	Grupo:gs_gerDOEM
	Grupo:gs_doEM
	Grupo:Invitados
	Grupo:Builtin
Mail:rocio.franco@elmejor.com.py
Cedula:LP09SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4012911
PrimerNombre:Oscar Rodrigo
Segundo Nombre:De León Rivas
title:Programador Informatico
department:Informatica
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_informaticaLP
	Grupo:Informatica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:Informatica
	Grupo:gs_it
Mail:oscar.deleon@laplata.com.py
Cedula:PCFACT01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:1625826
PrimerNombre:Adela
Segundo Nombre:Britez Cañete
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:adela.britez@elmejor.com.py
Cedula:mario.troche
PrimerNombre:Mario Agustin
Segundo Nombre:Troche Ortellado
title:GERENTE COMERCIAL
department:COMERCIAL
company:PROACTIF CARE
directReports:[]
Miembro de:
	Grupo:Ssl vpn PC
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:gs_comercialPC
Mail:mario.troche@proactif.com.py
Cedula:5182623
PrimerNombre:Juan Agustin
Segundo Nombre:Torres Miranda
title:Logistica
department:Logistica
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Logistica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_logisticaLP
Mail:juan.torres@laplata.com.py
Cedula:LPIT04$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP27SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP08SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP21SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5002170
PrimerNombre:Patricia Belen
Segundo Nombre:Balbuena Duarte
title:Asesor Comercial Proactif Care
department:Comercial
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_comercialPC
Mail:patricia.balbuena@proactif.com.py
Cedula:2192047
PrimerNombre:Carlos Quintin
Segundo Nombre:Cristaldo Alvarez
title:Asesor Comercial
department:Comercial
company:Proactif Care SA
directReports:[]
Miembro de:
	Grupo:Internet intermedio con RS
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial - Proactif
	Grupo:gs_invitados
	Grupo:Ventas - Proactif
	Grupo:gs_proactif
	Grupo:gs_comercialPC
Mail:carlos.cristaldo@proactif.com.py
Cedula:PCCOMER05$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP03SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMPRO$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4440055
PrimerNombre:Gustavo Ruben
Segundo Nombre:Acuña Martinez
title:Cobrador Proactif Care
department:Administracion PC
company:Proactif Care S.A.
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:gustavo.acuna@proactif.com.py
Cedula:LP18SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3864187
PrimerNombre:Aldo Rene
Segundo Nombre:Rivas Ojeda
title:Auxiliar Informatico
department:Informatica
company:El Mejor S.R.L.
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:BPM - Grupo Baudelet
	Grupo:Informatica
	Grupo:El Mejor
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:aldo.rivas@elmejor.com.py
Cedula:4627017
PrimerNombre:Sebastian Fernando
Segundo Nombre:Salinas Reitzenstein
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc12
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:sebastian.salinas@laplata.com.py
Cedula:5495734
PrimerNombre:Ruth Noelia
Segundo Nombre:Lopez Caceres
title:Auxiliar de Salarios
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
Mail:ruth.lopez@elmejor.com.py
Cedula:ricardo.cabral
PrimerNombre:Ricardo David
Segundo Nombre:Cabral Yegros
title:Gerente de Operaciones
department:Operaciones Proactif
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Gerencias - Proactif
	Grupo:gs_invitados
	Grupo:gs_proactif
Mail:ricardo.cabral@proactif.com.py
Cedula:EMINFO$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3982826
PrimerNombre:Maria Elena
Segundo Nombre:Benitez Gimenez
title:Atencion Showroom
department:Comercial
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
	Grupo:gs_proactif
Mail:maria.benitez@proactif.com.py
Cedula:4800988
PrimerNombre:Victor Hugo
Segundo Nombre:Melo Amarilla
title:Auxiliar de Recursos Logísticos
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:victor.melo@elmejor.com.py
Cedula:EMAUD001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCOMER01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:rolando.bogado
PrimerNombre:Rolando Javier
Segundo Nombre:Bogado Gimenez
title:Auxiliar Informatico
department:Informatica
company:El Mejor S.R.L.
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:BPM - Grupo Baudelet
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:rolando.bogado@elmejor.com.py
Cedula:EMIT55$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCC001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:notificacioneslp
PrimerNombre:Notificaciones LP
Segundo Nombre:Envio de mails
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:notificacioneslp@laplata.com.py
Cedula:5388347
PrimerNombre:Mary Carmen
Segundo Nombre:Dominguez Sandoval
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
Mail:mary.dominguez@teconviene.com.py
Cedula:4794903
PrimerNombre:Zara Mariela
Segundo Nombre:Romero Dionisi
title:Auxiliar de Recursos Humanos
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:gs_rrhhEM
Mail:zara.romero@elmejor.com.py
Cedula:EMPM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMRRHH11$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4364293
PrimerNombre:Diosnel
Segundo Nombre:Lopez Arce
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc16
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:diosnel.lopez@laplata.com.py
Cedula:LP39SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:conformidadle
PrimerNombre:Conformidad -
Segundo Nombre:Los especialistas EM
title:Conformidad - Los Especialistas
department:[]
company:El Mejor
directReports:[]
Miembro de:
Mail:conformidadle@elmejor.com.py
Cedula:3554830
PrimerNombre:Julieta Soledad
Segundo Nombre:Valdez Centurion
title:Vendedora de Salon
department:Comercial
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Ssl vpn PROV
	Grupo:Proactif Care
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Tienda Proactif
	Grupo:gs_proactif
Mail:julieta.valdez@proactif.com.py
Cedula:EMIT007$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMRESERVA$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4811794
PrimerNombre:Fernando Ariel
Segundo Nombre:Gomez Gonzalez
title:Encargado
department:Comercial
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc39
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:fernando.gomez@laplata.com.py
Cedula:4164270
PrimerNombre:Beto Orlando
Segundo Nombre:Gonzalez Rodriguez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc40
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:beto.gonzalez@laplata.com.py
Cedula:servicionav
PrimerNombre:Servicio NAV
Segundo Nombre:Dynamics
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:User Impersonate
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores
	Grupo:Builtin
Mail:servicionav@grupobaudelet.com
Cedula:4669221
PrimerNombre:Oscar Javier
Segundo Nombre:Lezcano Rodriguez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
Mail:oscar.lezcano@laplata.com.py
Cedula:EMOPE006$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:6154493
PrimerNombre:Francisco Javier
Segundo Nombre:Ortiz Gaete
title:Gestor Administrativo
department:Administracion
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_AdministracionLP
Mail:francisco.ortiz@laplata.com.py
Cedula:4633028
PrimerNombre:ANGEL MILCIADES
Segundo Nombre:DIAZ IRALA
title:Asesor Comercial
department:Comercial Proactif
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:User Impersonate
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_comercialPC
Mail:angel.diaz@proactif.com.py
Cedula:EMCAP002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3861013
PrimerNombre:Andrea Carolina
Segundo Nombre:Cardozo Quinonez
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center
	Grupo:gs_contactEM
	Grupo:gs_callEM
	Grupo:El Mejor
Mail:andrea.cardozo@elmejor.com.py
Cedula:3765514
PrimerNombre:Florencia Daiana
Segundo Nombre:Miranda Carpio
title:Representante de Atención al Cliente
department:GT
company:EL MEJOR
directReports:[]
Miembro de:
Mail:florencia.miranda@teconviene.com.py
Cedula:PCIT01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP02SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:6635266
PrimerNombre:David Fernando
Segundo Nombre:Ramirez Teme
title:Encargado Suc. 29
department:COMERCIAL
company:LA PLATA
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc29
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:david.ramirez@laplata.com.py
Cedula:3522363
PrimerNombre:Hugo Ricardo
Segundo Nombre:Gavilan
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:hugo.gavilan@elmejor.com.py
Cedula:EMADMT$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5399162
PrimerNombre:Reinaldo
Segundo Nombre:Benitez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc35
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:reinaldo.benitez@laplata.com.py
Cedula:PCCOME06$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4981286
PrimerNombre:Francisco
Segundo Nombre:Benitez Denis
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
Mail:francisco.benitez@teconviene.com.py
Cedula:LP44SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP05SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP32SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:7204123
PrimerNombre:Willian David
Segundo Nombre:Robles Cabrera
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
Mail:willian.robles@laplata.com.py
Cedula:LP16SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:6050766
PrimerNombre:Pamela Jazmín
Segundo Nombre:Marban Mongelos
title:Asistente Comercial
department:Comercial
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:BPM - Grupo Baudelet
	Grupo:gs_it
Mail:pamela.marban@proactif.com.py
Cedula:6169300
PrimerNombre:Carlos Antonio
Segundo Nombre:Britez Franco
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc37
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:carlos.britez@laplata.com.py
Cedula:4619764
PrimerNombre:Magali Santacruz
Segundo Nombre:Urrutia
title:OPERADORA CONTACT CENTER
department:Administración
company:Proactif Care S.A.
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_contactPC
Mail:magali.santacruz@proactif.com.py
Cedula:4577873
PrimerNombre:Hernan Dario
Segundo Nombre:Mendiola Centurion
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
Mail:hernan.mendiola@teconviene.com.py
Cedula:EMOPE004$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EXCHANGE$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Managed Availability Servers
	Grupo:Exchange Install Domain Servers
	Grupo:Microsoft Exchange System Objects
	Grupo:Exchange Trusted Subsystem
	Grupo:Exchange Servers
Mail:[]
Cedula:5928818
PrimerNombre:Guadalupe
Segundo Nombre:Nunez Marecos
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
Mail:guadalupe.nunez@elmejor.com.py
Cedula:LP07SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:HealthMailbox9904130
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox9904130db71d4f35984554d1cdae87aa@grupobaudelet.com
Cedula:HealthMailbox75e968b
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox75e968b5a769486fae83424b8c4a3d5f@grupobaudelet.com
Cedula:HealthMailboxe72b159
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxe72b159ddbd24934b955ec8f4ffb457f@grupobaudelet.com
Cedula:HealthMailboxdf58445
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxdf58445e8c6a47f8aee3f91eeb3383b5@grupobaudelet.com
Cedula:HealthMailboxe391629
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxe391629206ae4f4e9b88518248cd80d6@grupobaudelet.com
Cedula:HealthMailbox9e92cea
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox9e92cea7f78e46639d096948e1d2e941@grupobaudelet.com
Cedula:HealthMailbox6b2f4e0
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox6b2f4e0c90044b4c80fd4509f0c9d848@grupobaudelet.com
Cedula:HealthMailbox019ca22
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox019ca2291d8c44c7af8a67a049de82a3@grupobaudelet.com
Cedula:HealthMailboxedd4447
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxedd4447f0b2a4e5c86c05bf3f2cdafc7@grupobaudelet.com
Cedula:HealthMailbox71dbe44
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox71dbe44299924c51a156e14b76f0523b@grupobaudelet.com
Cedula:HealthMailbox0a6c316
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox0a6c3166dc224f0ba8343bcbeb5ad10a@grupobaudelet.com
Cedula:HealthMailboxe42b030
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxe42b0306b66844149e32447e3c9ff678@grupobaudelet.com
Cedula:HealthMailbox853e026
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox853e026bcea44d93a7231709aa109dd4@grupobaudelet.com
Cedula:HealthMailbox1f425b1
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox1f425b13d7b24ecdb87af9b3af20d92b@grupobaudelet.com
Cedula:SM_b9546649a2224392a
PrimerNombre:[]
Segundo Nombre:SystemMailbox{D0E409A0-AF9B-4720-92FE-AAC869B0D201}
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:SystemMailbox{D0E409A0-AF9B-4720-92FE-AAC869B0D201}@teconviene.com.py
Cedula:SM_72c29e1f679944ad9
PrimerNombre:[]
Segundo Nombre:SystemMailbox{2CE34405-31BE-455D-89D7-A7C7DA7A0DAA}
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:SystemMailbox{2CE34405-31BE-455D-89D7-A7C7DA7A0DAA}@teconviene.com.py
Cedula:SM_b4faa520db96490da
PrimerNombre:[]
Segundo Nombre:SystemMailbox 8cc370d3-822a-4ab8-a926-bb94bd0641a9
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:SystemMailbox{8cc370d3-822a-4ab8-a926-bb94bd0641a9}@teconviene.com.py
Cedula:HealthMailbox1b8122e
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox1b8122eb02444b3498f3a3dcbe93a41d@grupobaudelet.com
Cedula:HealthMailboxcfe928f
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxcfe928f07d4b42d38c5b37c42cb8a77d@grupobaudelet.com
Cedula:HealthMailboxb073325
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxb073325619664c88b3764947879fceba@grupobaudelet.com
Cedula:HealthMailbox5994894
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox5994894a7db94cf584e6903bcce0da86@grupobaudelet.com
Cedula:HealthMailbox56c1de1
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox56c1de13b54845508f2fea74e7ecfb1a@grupobaudelet.com
Cedula:HealthMailbox5fbc8f7
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox5fbc8f785ac249aebe68315212bb5532@grupobaudelet.com
Cedula:HealthMailboxfa5b3aa
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxfa5b3aa1dba340af84b5fa566ecd71fd@grupobaudelet.com
Cedula:HealthMailbox88ce152
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox88ce152732b5417c82801b47cc479a1f@grupobaudelet.com
Cedula:HealthMailbox950d70c
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox950d70c8fa8a45df969be07bfddac502@grupobaudelet.com
Cedula:HealthMailboxa15ccf7
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxa15ccf71d74142e1b59876213d538165@grupobaudelet.com
Cedula:HealthMailbox622779e
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox622779e24c9a4b04bea228e769ae9b56@grupobaudelet.com
Cedula:4746875
PrimerNombre:Alberto Ismael
Segundo Nombre:Velazquez Franco
title:Auxiliar Contable
department:ADMINISTRACION
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Administracion - El Mejor
	Grupo:El Mejor
	Grupo:gs_administracionEM
Mail:alberto.velazquez@elmejor.com.py
Cedula:usuario.pc
PrimerNombre:UsuarioProactif
Segundo Nombre:Acceso
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3179731
PrimerNombre:Marta Sara
Segundo Nombre:Montiel Ojeda
title:Asesora Comercial
department:Comercial Proactif
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_comercialPC
Mail:marta.montiel@proactif.com.py
Cedula:4666880
PrimerNombre:Jorge Romario
Segundo Nombre:Riveros Benitez
title:Logistica
department:Logistica
company:La Plata
directReports:[]
Miembro de:
Mail:[]
Cedula:HealthMailbox4a8f9ef
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox4a8f9efc9842469987c25f9b410e594b@grupobaudelet.com
Cedula:HealthMailbox975d8dd
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox975d8ddc6fdf428392d6415265f1c578@grupobaudelet.com
Cedula:HealthMailbox35e134b
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox35e134b198cf4257adaecd5a0381e62d@grupobaudelet.com
Cedula:HealthMailbox873edba
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox873edba82e0845bebc2dc122cb4dce1a@grupobaudelet.com
Cedula:5150008
PrimerNombre:gregorio gonzalez
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:SRVHYPERV$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:SM_a2260cdb982243a29
PrimerNombre:[]
Segundo Nombre:Migration.8f3e7716-2011-43e4-96b1-aba62d229136
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:Migration.8f3e7716-2011-43e4-96b1-aba62d229136@teconviene.com.py
Cedula:5080920
PrimerNombre:Ana Judith
Segundo Nombre:Cabrera Jara
title:Representante de Servicios
department:Contact Center
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center - La Plata
	Grupo:Avisos BPM LP
	Grupo:gs_contactLP
	Grupo:La Plata
Mail:ana.cabrera@laplata.com.py
Cedula:PCCOMER10$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5270794
PrimerNombre:Perla Elizabeth
Segundo Nombre:Caballero Ruiz Diaz
title:Auxiliar de Recursos Humanos
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
Mail:perla.caballero@teconviene.com.py
Cedula:EMAUXMKT$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4307077
PrimerNombre:Daniel Agustin
Segundo Nombre:Samaniego Servin
title:Ejecutivo Comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:daniel.samaniego@elmejor.com.py
Cedula:4617579
PrimerNombre:Ayessa
Segundo Nombre:Ayala Samaniego
title:Auxiliar de Comunicaciones
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
Mail:ayessa.ayala@teconviene.com.py
Cedula:5222095
PrimerNombre:Junior Damian
Segundo Nombre:Gimenez Rodas
title:Auxiliar de TI
department:Informatica
company:EL MEJOR S.R.L.
directReports:[]
Miembro de:
	Grupo:backofficeem
	Grupo:Monitoreo
	Grupo:gs_elmejor_all
	Grupo:Soporte TIC EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Monitoreo Infraestructura TIC
	Grupo:Organization Management
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores
	Grupo:Builtin
Mail:junior.gimenez@elmejor.com.py
Cedula:5320132
PrimerNombre:Richard Hernan
Segundo Nombre:Vera Lopez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc31
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:richard.vera@laplata.com.py
Cedula:4937176
PrimerNombre:Hugo Alejandro
Segundo Nombre:Cabral Amarilla
title:Auxiliar Informatica
department:Informatica Proactif
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:BPM - Grupo Baudelet
	Grupo:gs_it
Mail:hugo.cabral@proactif.com.py
Cedula:EMRRHH006$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMCOMER012$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCADM6$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4436767
PrimerNombre:Cathia Cecilia
Segundo Nombre:Mercado Gonzalez
title:Auxiliar de Administracion Comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:backofficeem
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Licitaciones_EM
	Grupo:Grupo Impulsor EM
	Grupo:Comercial - El Mejor
	Grupo:gs_comercialEM
	Grupo:gs_El_Mejor
Mail:cathia.mercado@elmejor.com.py
Cedula:123456
PrimerNombre:usuario_uno
Segundo Nombre:[]
title:Asesor Comercial
department:Comercial
company:La Plata
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
Mail:usuario_uno@laplata.com.py
Cedula:456789
PrimerNombre:usuario_dos
Segundo Nombre:[]
title:Asesor Comercial
department:Comercial
company:La Plata
directReports:[]
Miembro de:
	Grupo:Grupo Baudelet
Mail:usuario_dos@laplata.com.py
Cedula:3998459
PrimerNombre:Julio Carlos
Segundo Nombre:Orue Ortiz
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc03
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:julio.orue@laplata.com.py
Cedula:4495388
PrimerNombre:Virgilio Antonio
Segundo Nombre:Gavilan Ramirez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc42
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:virgilio.gavilan@laplata.com.py
Cedula:EMOPE013$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMIT001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4604937
PrimerNombre:Gabriel Antonio
Segundo Nombre:Cantero Osorio
title:Servicio Técnico - Proactif
department:Servicio Técnico
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:gabriel.cantero@proactif.com.py
Cedula:LP19SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5215929
PrimerNombre:Dario
Segundo Nombre:Vera Colman
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:dario.vera@elmejor.com.py
Cedula:LP45SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4850581
PrimerNombre:Jose Ramon
Segundo Nombre:Benitez Sandoval
title:Gestor Administrativo
department:Administracion
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_AdministracionLP
Mail:jose.benitez@laplata.com.py
Cedula:4992792
PrimerNombre:Sergio Rolando
Segundo Nombre:Irala Diaz
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc17
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:sergio.irala@laplata.com.py
Cedula:3547938
PrimerNombre:Carmen
Segundo Nombre:Lopez de Arrua
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:carmen.lopez@elmejor.com.py
Cedula:5149559
PrimerNombre:Juan Fernando
Segundo Nombre:Baez Nunez
title:Auxiliar Adm - Los especialistas
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:juan.baez@elmejor.com.py
Cedula:santiago.fa
PrimerNombre:Santiago Tomas
Segundo Nombre:Fernandez Arroyo
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:santiago.fa@spartanchemical.com.ar
Cedula:javier.fa
PrimerNombre:Javier
Segundo Nombre:Fernandez Arroyo
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:javier.fa@spartanchemical.com.ar
Cedula:3831295
PrimerNombre:Carlos David
Segundo Nombre:Ibarra Mora
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc38
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:carlos.ibarra@laplata.com.py
Cedula:EMCOMER013$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4843517
PrimerNombre:Tomas Ovidio
Segundo Nombre:Lesme
title:Ejecutivo de Ventas Ocasionales
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial Ocasionales
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:tomas.lesme@elmejor.com.py
Cedula:PCIT02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:cintia.da
PrimerNombre:Cintia
Segundo Nombre:De Anton
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:cintia.da@spartanchemical.com.ar
Cedula:matias.t
PrimerNombre:Matias
Segundo Nombre:Tagliotti
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:matias.t@spartanchemical.com.ar
Cedula:gaston.s
PrimerNombre:Gaston
Segundo Nombre:Stockman
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:gaston.s@spartanchemical.com.ar
Cedula:LPAUD001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3871043
PrimerNombre:Leticia Soraya
Segundo Nombre:Aguero Pereira
title:Auxiliar de Recursos Humanos
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:RRHH - El Mejor
	Grupo:El Mejor
	Grupo:gs_rrhhEM
Mail:leticia.aguero@elmejor.com.py
Cedula:3663500
PrimerNombre:Porfiria
Segundo Nombre:Rios
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:porfiria.rios@elmejor.com.py
Cedula:4218026
PrimerNombre:Ilda Cristina
Segundo Nombre:Riveros Morales
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:ilda.riveros@elmejor.com.py
Cedula:2267101
PrimerNombre:Jorge Luis
Segundo Nombre:Arguello Cardenas
title:Asesor Comercial
department:Comercial
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_comercialPC
Mail:jorge.arguello@proactif.com.py
Cedula:5927494
PrimerNombre:Arnaldo
Segundo Nombre:Bruno Armoa
title:Auditoria
department:Auditoria
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_auditoriaLP
Mail:arnaldo.bruno@laplata.com.py
Cedula:invitadolp
PrimerNombre:Invitado
Segundo Nombre:LP
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:[]
Cedula:MSOL_fb7b8954abd7
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:hector.m
PrimerNombre:Hector
Segundo Nombre:Magrini
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:hector.m@spartanchemical.com.ar
Cedula:EMMKT$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:fanny.dominguez
PrimerNombre:Fanny
Segundo Nombre:Dominguez
title:Sub Gerente de Operaciones
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:coordinadoras
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:gs_CoorFisEM
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:fanny.dominguez@elmejor.com.py
Cedula:SHOWROOM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:cristian.cabanellas
PrimerNombre:Cristian Copp
Segundo Nombre:Cabanellas Esteche
title:Gerente de TIC
department:Tecnologías de la Información y Comunicación
company:EL MEJOR
directReports:CN=David Ariel Hermosa Pereira,OU=IT,OU=GrupoBaudelet,DC=grupobaudelet,DC=com
Miembro de:
	Grupo:Monitoreo
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn INFRA
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Gerencias - El Mejor
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
Mail:cristian.cabanellas@elmejor.com.py
Cedula:PCIT03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:digipar.test
PrimerNombre:Digipar
Segundo Nombre:Holding Tests
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5013484
PrimerNombre:Clara Azucena
Segundo Nombre:Soria Soria
title:Representante de Servicios
department:Contact Center
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center - La Plata
	Grupo:Avisos BPM LP
	Grupo:gs_contactLP
	Grupo:La Plata
Mail:azucena.soria@laplata.com.py
Cedula:LP36SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:digiparlp.test
PrimerNombre:Digipar LP
Segundo Nombre:Holding Tests
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:digiparlp.test@laplata.com.py
Cedula:HealthMailboxe99eed9
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxe99eed9dda8140f19e0f9a8fa3ee32ec@grupobaudelet.com
Cedula:HealthMailbox642ffd3
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox642ffd33c5134c52bcff392c046bdafc@grupobaudelet.com
Cedula:HealthMailbox60117eb
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox60117ebb96b9444aa90c875246cf58ed@grupobaudelet.com
Cedula:HealthMailbox3c8b0e0
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox3c8b0e08868e4b6e81361f57c213f377@grupobaudelet.com
Cedula:HealthMailbox85aac97
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox85aac97913d6423298b7eba1e97f00c6@grupobaudelet.com
Cedula:HealthMailbox0614f27
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox0614f27dc77e4b2d88bdf5e2e80ba773@grupobaudelet.com
Cedula:HealthMailboxc0ac809
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxc0ac80900a5f429eac180bdb6db2c45b@grupobaudelet.com
Cedula:HealthMailboxd9e0fca
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxd9e0fca174744fb9b1dcefc8ff339d49@grupobaudelet.com
Cedula:HealthMailbox4671236
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox4671236598da4c61acf330e3e987b5b5@grupobaudelet.com
Cedula:HealthMailbox3f21138
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox3f2113885338404bb5d75b0fcc1664fe@grupobaudelet.com
Cedula:HealthMailbox28c817b
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox28c817b4fc2843bcbfd5e7f5d44930b5@grupobaudelet.com
Cedula:HealthMailbox7320fbd
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox7320fbdf3a0b411dac653dd5e5eb3c9e@grupobaudelet.com
Cedula:HealthMailbox7e379bc
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox7e379bcbc11a4778843d27b5765b7cef@grupobaudelet.com
Cedula:HealthMailbox78634f8
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox78634f8969854a06a3c7c7135fb23ca8@grupobaudelet.com
Cedula:HealthMailboxc3e49f5
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxc3e49f5bf9f04315812105fdb4d9a966@grupobaudelet.com
Cedula:HealthMailbox54fbad1
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox54fbad12653e42938adc2edee204d875@grupobaudelet.com
Cedula:HealthMailboxdb86c84
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxdb86c847f3c84ce0b9cf37a9302216e8@grupobaudelet.com
Cedula:HealthMailbox570210c
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox570210c4a0c148aa95bc0ac73f5eb99f@grupobaudelet.com
Cedula:HealthMailbox41747a4
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox41747a4210464cd280c7d25be11c0e3e@grupobaudelet.com
Cedula:HealthMailbox828597a
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox828597ae8d204f1aaf5ecb16febf409c@grupobaudelet.com
Cedula:HealthMailbox4102f8b
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox4102f8b281fd4f82bbbc213b73e4572d@grupobaudelet.com
Cedula:HealthMailbox2e6d345
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailbox2e6d3451b46d41ccba41b962c764aab8@grupobaudelet.com
Cedula:3479845
PrimerNombre:Mara Dinka
Segundo Nombre:Soljancic Samanez
title:Jefa de Comunicacion y Responsabilidad Social Empresarial
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Informaciones - Web EM
	Grupo:Newsletter
	Grupo:gs_marketingEM
	Grupo:Comercial - El Mejor
	Grupo:gs_comercialEM
Mail:mara.soljancic@teconviene.com.py
Cedula:LP06SUC02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGERTIC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPE026$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPAUD004$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:celeste.flores
PrimerNombre:Maria Celeste
Segundo Nombre:Flores
title:Administración
department:Administracion
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:Administracion - La Plata
	Grupo:La Plata
	Grupo:gs_AdministracionLP
Mail:celeste.flores@laplata.com.py
Cedula:2489522
PrimerNombre:Carlos Gabriel
Segundo Nombre:Oviedo Bogado
title:Asesor Comercial
department:Comercial Proactif
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:carlos.oviedo@proactif.com.py
Cedula:PCCOME1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPCC02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPADM01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:NOTEBOOK-HP-LIB$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMIT002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:willian.galeano
PrimerNombre:Willian
Segundo Nombre:Galeano Garcia
title:Coordinador de Infraestructuras y Plataformas
department:Informatica
company:EL MEJOR S.R.L.
directReports:[]
Miembro de:
	Grupo:Monitoreo
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Monitoreo Infraestructura TIC
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de empresas
	Grupo:Users
	Grupo:Administradores de esquema
	Grupo:Users
	Grupo:Administradores de Hyper-V
	Grupo:Builtin
	Grupo:Administradores
	Grupo:Builtin
Mail:willian.galeano@elmejor.com.py
Cedula:gustavo.alvarez
PrimerNombre:Gustavo Rodrigo
Segundo Nombre:Alvarez
title:Auditoria
department:Auditoria
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_auditoriaLP
Mail:gustavo.alvarez@laplata.com.py
Cedula:LPLOG02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:WIN10PRO64$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:pruebatic
PrimerNombre:Prueba
Segundo Nombre:Tecnologia
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
Mail:[]
Cedula:martin.p
PrimerNombre:Martin
Segundo Nombre:Pereyra
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:martin.p@spartanchemical.com.ar
Cedula:userldap
PrimerNombre:User
Segundo Nombre:Ldap
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PC-GG$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPCOM01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCADM01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5307975
PrimerNombre:Cesar David
Segundo Nombre:Marecos Farina
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc13
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:cesar.marecos@laplata.com.py
Cedula:pruebados
PrimerNombre:Prueba
Segundo Nombre:Dos
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:1234567
PrimerNombre:Usuario
Segundo Nombre:Tres
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:MQ_PRUEBATIC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4030330
PrimerNombre:Karen Beatriz
Segundo Nombre:Ojeda Aguilera
title:Asistente de Compras
department:Logistica
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:gs_invitados
	Grupo:gs_logisticaPC
Mail:karen.ojeda@proactif.com.py
Cedula:PCOP01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCFAC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5722186
PrimerNombre:Diego German
Segundo Nombre:Anazco
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
Mail:diego.anazco@elmejor.com.py
Cedula:PCOP03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCOP02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCOP04$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5019090
PrimerNombre:Federico Adrian
Segundo Nombre:Florentin
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc45
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:federico.florentin@laplata.com.py
Cedula:SM_3ec1d6fa29024d989
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:ResultadoBusqueda@teconviene.com.py
Cedula:PCIT2$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:pruebaspartan
PrimerNombre:Prueba
Segundo Nombre:Spartan
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:pruebaspartan@spartanchemical.com.ar
Cedula:EMCOORDSIS$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4197179
PrimerNombre:Josep Fabian
Segundo Nombre:Duarte Vega
title:Facturador Proactif
department:Facturacion
company:Proactif Care S.A.
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
Mail:josep.duarte@proactif.com.py
Cedula:3471637
PrimerNombre:Santiago Anibal
Segundo Nombre:Yegros Zaracho
title:Coordinador de Sistemas
department:Informatica
company:EL MEJOR S.R.L.
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:santiago.yegros@elmejor.com.py
Cedula:LPCAM01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:recepcion
PrimerNombre:Recepcion
Segundo Nombre:El Mejor
title:Representante de Atención al Cliente
department:GT
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio con RS
	Grupo:GrupoBaudelet
	Grupo:gs_gestiontalentoEM
	Grupo:Grupo Baudelet
	Grupo:Gestion de Talento
	Grupo:El Mejor
	Grupo:gs_doEM
Mail:recepcion@elmejor.com.py
Cedula:EMGERRRHH$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCSHOWROOM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPAUD05$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3466538
PrimerNombre:Carlos Augusto
Segundo Nombre:Rodriguez Acosta
title:Asesor Comercial
department:Comercial Proactif
company:Proactif Care S.A.
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:gs_comercialPC
Mail:carlos.rodriguez@proactif.com.py
Cedula:PCST$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCOP05$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:2178444
PrimerNombre:Juan Victor
Segundo Nombre:Gill Augusto
title:Asesor Comercial
department:Comercial
company:Proactif Care S.A.
directReports:[]
Miembro de:
	Grupo:Ssl vpn PC
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:gs_comercialPC
Mail:juan.gill@proactif.com.py
Cedula:PCADM02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP26SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMENCUES04$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMENCUES02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMENCUES01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:mariano.l
PrimerNombre:Mariano
Segundo Nombre:Leyes
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:mariano.l@spartanchemical.com.ar
Cedula:4796510
PrimerNombre:Maria Belén
Segundo Nombre:Fleitas Maidana
title:Auxiliar Informatico
department:Informatica
company:El Mejor S.R.L.
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:BPM - Grupo Baudelet
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:belen.fleitas@teconviene.com.py
Cedula:LP11SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPAUD02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4905534
PrimerNombre:Alan Jesus
Segundo Nombre:Zalazar Barrientos
title:Ejecutivo de Cuentas
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:alan.zalazar@elmejor.com.py
Cedula:EMDB6$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BAUDELETBPM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:BPMTESTING$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCIT04$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCOME05$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCIT05$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3764111
PrimerNombre:Jose Emilio
Segundo Nombre:Rodriguez Pessolani
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
Mail:jose.rodriguez@teconviene.com.py
Cedula:PCIT3$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCCOME07$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:1538762
PrimerNombre:Teresita
Segundo Nombre:Vera Benitez
title:Capacitadora
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:gs_operacionesEM
Mail:teresita.vera@elmejor.com.py
Cedula:2306280
PrimerNombre:Maria Nelida
Segundo Nombre:Benitez Pascua
title:Fiscal
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:nelida.benitez@elmejor.com.py
Cedula:3448710
PrimerNombre:Ema Ramona
Segundo Nombre:Colman
title:Capacitadora
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:gs_operacionesEM
Mail:ema.colman@elmejor.com.py
Cedula:3237632
PrimerNombre:Jorgelina
Segundo Nombre:Morinigo Aguirre
title:Capacitadora
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:gs_operacionesEM
Mail:jorgelina.morinigo@elmejor.com.py
Cedula:4368769
PrimerNombre:Alicia
Segundo Nombre:Prieto Medina
title:Capacitadora
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:gs_operacionesEM
Mail:alicia.prieto@elmejor.com.py
Cedula:5263813
PrimerNombre:Clemente
Segundo Nombre:Miranda Fernandez
title:Capacitadora
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:clemente.miranda@elmejor.com.py
Cedula:LPFB001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3528182
PrimerNombre:Diego Enrique
Segundo Nombre:Arce Torres
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_El_Mejor
Mail:diego@losespecialistas.com.py
Cedula:LP12SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GBCORPORATER$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GBDC1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMDEP02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMJEFMKT$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCAUX$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP34SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCAUX01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4503602
PrimerNombre:Victor Matias
Segundo Nombre:Medina Baez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:gs_suc46
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:victor.medina@laplata.com.py
Cedula:LP48SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4896453
PrimerNombre:Sergio Javier
Segundo Nombre:Ledesma Rodriguez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc01
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:sergio.ledesma@laplata.com.py
Cedula:5684206
PrimerNombre:Pedro Pastor
Segundo Nombre:Pavon Gonzalez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc21
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:pedro.pavon@laplata.com.py
Cedula:BAUDELETPROXY$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP30SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GBDBNT$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5745808
PrimerNombre:Yamila Ailen
Segundo Nombre:Duarte Almiron
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
Mail:[]
Cedula:7421265
PrimerNombre:MAURICIO
Segundo Nombre:MARMOL
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_comercialPC
Mail:mauricio.marmol@proactif.com.py
Cedula:ARCHIVOSEM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP47SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCIT4$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4989409
PrimerNombre:Luis Armando
Segundo Nombre:Colman Mora
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:luis.colman@elmejor.com.py
Cedula:PCIT5$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:7336033
PrimerNombre:Andrea
Segundo Nombre:Gauto
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:gs_proactif
Mail:andrea.gauto@proactif.com.py
Cedula:4839779
PrimerNombre:Sixto Antonio
Segundo Nombre:Ramirez Gonzalez
title:Logistica
department:Logistica
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Logistica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_logisticaLP
Mail:sixto.ramirez@laplata.com.py
Cedula:5612199
PrimerNombre:Rodrigo Fabian
Segundo Nombre:Valdez Aguero
title:Logistica
department:Logistica
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Logistica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_logisticaLP
Mail:rodrigo.valdez@laplata.com.py
Cedula:3254743
PrimerNombre:Manuel Alejandro
Segundo Nombre:Villanueva Roman
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet full
	Grupo:gs_invitados
	Grupo:gs_proactif
	Grupo:gs_comercialPC
Mail:manuel.villanueva@proactif.com.py
Cedula:2917245
PrimerNombre:Hugo Enrique
Segundo Nombre:Ayala Moreno
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:gs_invitados
	Grupo:gs_proactif
Mail:hugo.ayala@proactif.com.py
Cedula:PCCALIDAD$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMGERGRALADJ$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPADM04$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4117881
PrimerNombre:Chiara
Segundo Nombre:Lucantonio Oxilia
title:Auxiliar de Comunicaciones y RSE
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Informaciones - Web EM
	Grupo:Newsletter
	Grupo:gs_marketingEM
	Grupo:Comercial - El Mejor
	Grupo:gs_comercialEM
Mail:chiara.lucantonio@teconviene.com.py
Cedula:veambackup
PrimerNombre:Veam
Segundo Nombre:Backup
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de empresas
	Grupo:Users
	Grupo:Administradores de esquema
	Grupo:Users
	Grupo:Administradores de Hyper-V
	Grupo:Builtin
	Grupo:Administradores
	Grupo:Builtin
Mail:[]
Cedula:kaspersky
PrimerNombre:Kaspersky
Segundo Nombre:Security Center
title:Coordinador de Infraestructuras y Plataformas
department:Informatica
company:EL MEJOR S.R.L.
directReports:[]
Miembro de:
	Grupo:KLAdmins
	Grupo:Users
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de empresas
	Grupo:Users
	Grupo:Administradores de esquema
	Grupo:Users
	Grupo:Administradores de Hyper-V
	Grupo:Builtin
	Grupo:Administradores
	Grupo:Builtin
Mail:[]
Cedula:3553814
PrimerNombre:Liz Lorena
Segundo Nombre:Perez Clemotte
title:Auxiliar Representante de Servicio
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center
	Grupo:gs_contactEM
	Grupo:gs_callEM
	Grupo:El Mejor
Mail:liz.perez@elmejor.com.py
Cedula:LP43SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3972031
PrimerNombre:Carmen Romina
Segundo Nombre:Cabrera Alfonso
title:Capacitadora
department:Operaciones
company:El Mejor
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:carmen.cabrera@elmejor.com.py
Cedula:sharepoint
PrimerNombre:SharePoint
Segundo Nombre:Server
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Administradores
	Grupo:Builtin
Mail:[]
Cedula:shareservices
PrimerNombre:SharePoint
Segundo Nombre:Services
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Administradores
	Grupo:Builtin
Mail:[]
Cedula:4991601
PrimerNombre:Cesar Nicolas
Segundo Nombre:Peralta Barreto
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc36
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:cesar.peralta@laplata.com.py
Cedula:4710485
PrimerNombre:Nicolas Arthur
Segundo Nombre:Baudelet Gonzalez
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
Mail:nicolas.baudelet@proactif.com.py
Cedula:BAUDEBPMCHECK$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP28SUC02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3363343
PrimerNombre:Cynthia Elizabeth
Segundo Nombre:Duarte Escurra
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
	Grupo:gs_dirEM
Mail:cynthia.duarte@elmejor.com.py
Cedula:LPIT03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:SRVHYPERV01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:2126923
PrimerNombre:Blas
Segundo Nombre:Peralta
title:Jefe Logistica PC
department:Operaciones
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet intermedio
Mail:blas.peralta@proactif.com.py
Cedula:GBDBDEV$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCACOMERCIAL$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3542966
PrimerNombre:Diana
Segundo Nombre:Fernandez
title:OPERADORA CONTACT CENTER
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Internet intermedio con RS
	Grupo:Proactif Care
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_contactPC
Mail:diana.fernandez@proactif.com.py
Cedula:4815716
PrimerNombre:Maria Yissel
Segundo Nombre:Ysaci Rodriguez
title:OPERADORA CONTACT CENTER
department:CONTACT CENTER
company:[]
directReports:[]
Miembro de:
	Grupo:Internet intermedio con RS
	Grupo:Proactif Care
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial - Proactif
	Grupo:Ventas - Proactif
	Grupo:gs_contactPC
Mail:maria.ysaci@proactif.com.py
Cedula:spartan
PrimerNombre:Spartan
Segundo Nombre:SQL
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_it
Mail:[]
Cedula:5704137
PrimerNombre:Virginia
Segundo Nombre:Argana
title:CAPACITADOR TECNICO
department:DO
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:virginia.argana@elmejor.com.py
Cedula:1541257
PrimerNombre:Laura Isabel
Segundo Nombre:Sanabria Melgarejo
title:Asesora Comercial
department:Comercial
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:gs_comercialPC
Mail:laura.sanabria@proactif.com.py
Cedula:4799188
PrimerNombre:Christian
Segundo Nombre:Aranda
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
Mail:christian.aranda@elmejor.com.py
Cedula:GBCORELPTEST$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3573154
PrimerNombre:Nicolas
Segundo Nombre:Domecq Caballero
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
Mail:nicolas.domecq@teconviene.com.py
Cedula:GBFABRICASOFT02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:fabricasw
PrimerNombre:Fabrica
Segundo Nombre:Software
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Ssl vpn FABRICA
Mail:[]
Cedula:capacitacion
PrimerNombre:Capacitacion
Segundo Nombre:Proactif
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:3854753
PrimerNombre:Christian
Segundo Nombre:Rodriguez Rivas
title:Gestion de Calidad
department:Operaciones
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
	Grupo:Internet full
	Grupo:gs_invitados
	Grupo:gs_proactif
	Grupo:gs_administracionPC
Mail:christian.rodriguez@proactif.com.py
Cedula:LP00SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP04SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMOPECDE01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GBTASEM$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GBCORELP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:infoem
PrimerNombre:Infoem
Segundo Nombre:EM
title:[]
department:Informatica
company:El Mejor S.R.L.
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:GTIC
	Grupo:Informatica - El Mejor
	Grupo:Grupo Impulsor EM
	Grupo:BPM - Grupo Baudelet
	Grupo:Informatica
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:infoem@grupobaudelet.com
Cedula:lucas.v
PrimerNombre:Lucas Fabian
Segundo Nombre:Venturi
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Informaciones Web - SA
Mail:lucas.v@spartanchemical.com.ar
Cedula:fabricasw02
PrimerNombre:Fabrica
Segundo Nombre:Software 02
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Ssl vpn FABRICA
Mail:[]
Cedula:fabricasw03
PrimerNombre:Fabrica
Segundo Nombre:Software 03
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Ssl vpn FABRICA
Mail:[]
Cedula:GBFABRICASOFT03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GBFABRICASOFT04$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GBDBT_OLD$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:ARCHIVOSPC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4372953
PrimerNombre:Fredy
Segundo Nombre:Aguilera Colman
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc30
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:fredy.aguilera@laplata.com.py
Cedula:6010471
PrimerNombre:Pablo Osmar
Segundo Nombre:Caballero Nunez
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center
	Grupo:gs_contactEM
	Grupo:gs_callEM
	Grupo:El Mejor
Mail:pablo.caballero@elmejor.com.py
Cedula:jennifer.prette
PrimerNombre:Jennifer
Segundo Nombre:Prette
title:Asistente de Dirección
department:[]
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_gerOperacionesEM
	Grupo:gs_operacionesEM
Mail:jennifer.prette@elmejor.com.py
Cedula:vera.martinez
PrimerNombre:Vera Lucia
Segundo Nombre:Martinez Lugo
title:Jefa de Comunicacion y Responsabilidad Social Empresarial
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Informaciones - Web EM
	Grupo:Newsletter
	Grupo:gs_marketingEM
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:vera.martinez@elmejor.com.py
Cedula:federico.c
PrimerNombre:Federico
Segundo Nombre:Campos
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Informaciones Web - SA
	Grupo:Administracion -Spartan Argentina
Mail:federico.c@spartanchemical.com.ar
Cedula:AAD_5f852725c268
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Usuarios
	Grupo:Builtin
Mail:[]
Cedula:13723549
PrimerNombre:Anielly
Segundo Nombre:Teixeira
title:auxiliar de administracion comercial
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:cambiodehorario
	Grupo:cambio de horario
	Grupo:backofficeem
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Licitaciones_EM
	Grupo:Grupo Impulsor EM
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
	Grupo:gs_El_Mejor
Mail:anielly.teixeira@elmejor.com.py
Cedula:EMGERRRHH1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:javier.fernandez
PrimerNombre:Javier
Segundo Nombre:Fernandez
title:Gerente de Adm de RRHH
department:RRHH
company:EL MEJOR
directReports:['CN=Jose Daniel Aveiro Sanchez,OU=RRHH,OU=El Mejor,OU=GrupoBaudelet,DC=grupobaudelet,DC=com', 'CN=Diego Alejandro Duarte Viveros,OU=RRHH,OU=El Mejor,OU=GrupoBaudelet,DC=grupobaudelet,DC=com']
Miembro de:
	Grupo:SSO RRHH -El Mejor
	Grupo:SSO RRHH - El Mejor
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Grupo Impulsor EM
	Grupo:Informaciones - Web EM
	Grupo:Etica - El Mejor
	Grupo:RRHH - El Mejor
	Grupo:Gerencias - El Mejor
	Grupo:El Mejor
	Grupo:gs_gerRRHHEM
	Grupo:gs_rrhhEM
Mail:javier.fernandez@elmejor.com.py
Cedula:6068800
PrimerNombre:Salomon Ezequiel
Segundo Nombre:Martinez
title:Ejecutivo de Ventas Ocasionales
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Comercial Ocasionales
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:[]
Cedula:LP46SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:ariel.rodriguez
PrimerNombre:Ariel Sebastian
Segundo Nombre:Rodriguez Ayala
title:Auxiliar de Salud y Seguridad Ocupacional
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:SSO RRHH -El Mejor
	Grupo:SSO RRHH - El Mejor
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_operacionesEM
	Grupo:gs_rrhhEM
Mail:ariel.rodriguez@elmejor.com.py
Cedula:santiago.q
PrimerNombre:Santiago Abel
Segundo Nombre:Quiñones
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:santiago.q@spartanchemical.com.ar
Cedula:4656859
PrimerNombre:Gustavo Daniel
Segundo Nombre:Veron Gonzalez
title:Auditoria
department:Auditoria
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_auditoriaLP
Mail:gustavo.veron@laplata.com.py
Cedula:4942339
PrimerNombre:Mario Antonio
Segundo Nombre:Barboza Samudio
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc43
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:mario.barboza@laplata.com.py
Cedula:fabricasw04
PrimerNombre:Fabrica
Segundo Nombre:Software 04
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Ssl vpn FABRICA
Mail:[]
Cedula:LPIT02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GBFABRICASOFT$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PedidosProactif
PrimerNombre:PedidosProactif
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:PedidosProactif@proactif.com.py
Cedula:3496120
PrimerNombre:Silvana Alejandra
Segundo Nombre:Bordon Rojas
title:Auxiliar de Marketing
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Informaciones - Web EM
	Grupo:Newsletter
	Grupo:gs_marketingEM
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
Mail:silvana.bordon@elmejor.com.py
Cedula:6307267
PrimerNombre:Evelin Marlene
Segundo Nombre:Gimenez Gimenez
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center
	Grupo:gs_contactEM
	Grupo:gs_callEM
	Grupo:El Mejor
Mail:evelin.gimenez@elmejor.com.py
Cedula:EMGERCOMER1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:bizagi.modelador
PrimerNombre:Bizagi
Segundo Nombre:Modelador
title:[]
department:Informatica
company:El Mejor S.R.L.
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:GTIC
	Grupo:Informatica - El Mejor
	Grupo:Grupo Impulsor EM
	Grupo:BPM - Grupo Baudelet
	Grupo:Informatica
	Grupo:gs_it
	Grupo:Administradores
	Grupo:Builtin
Mail:bizagi.modelador@elmejor.com.py
Cedula:LPADM03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5419069
PrimerNombre:Edgar Osvaldo
Segundo Nombre:Spelt Ojeda
title:Analista de Infraestructuras y Plataformas
department:Tecnologías de la Información y Comunicación
company:EL MEJOR S.R.L.
directReports:[]
Miembro de:
	Grupo:Sucursal 49 - La Plata
	Grupo:Users
	Grupo:backofficeem
	Grupo:Monitoreo
	Grupo:gs_elmejor_all
	Grupo:Soporte TIC EM
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Monitoreo Infraestructura TIC
	Grupo:GTIC
	Grupo:Informatica - El Mejor
	Grupo:Informatica
	Grupo:El Mejor
	Grupo:Organization Management
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores
	Grupo:Builtin
Mail:edgar.spelt@elmejor.com.py
Cedula:4275371
PrimerNombre:Gilberto Ariel
Segundo Nombre:Melgarejo Paiva
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc05
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:gilberto.melgarejo@laplata.com.py
Cedula:GBFABRICASOFT05$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP50SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:fabricasw05
PrimerNombre:Fabrica Software 05
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Ssl vpn FABRICA
	Grupo:gs_it
Mail:[]
Cedula:5316876
PrimerNombre:Cynthia Maria Teresita
Segundo Nombre:Mendez Garcete
title:Encargado de Marketing
department:Desarrollo Comercial
company:La Plata
directReports:[]
Miembro de:
Mail:cynthia.mendez@teconviene.com.py
Cedula:miguel.ramirez
PrimerNombre:Miguel Angel
Segundo Nombre:Ramirez Portillo
title:Encargado de Marketing
department:Desarrollo Comercial
company:La Plata
directReports:[]
Miembro de:
Mail:miguel.ramirez@teconviene.com.py
Cedula:fernando.g
PrimerNombre:Fernando
Segundo Nombre:Giorgi
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
Mail:fernando.g@spartanchemical.com.ar
Cedula:GTEGRAL2$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GERTAL$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:GERADM1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5020918
PrimerNombre:Carlos Javier
Segundo Nombre:Barboza Cabanas
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
Mail:carlos.barboza@laplata.com.py
Cedula:3463472
PrimerNombre:Diego Alejandro
Segundo Nombre:Duarte Viveros
title:Analista de Salarios
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:RRHH - El Mejor
	Grupo:El Mejor
	Grupo:gs_rrhhEM
Mail:diego.duarte@elmejor.com.py
Cedula:LPCC03$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:6554985
PrimerNombre:Patricia Beatriz
Segundo Nombre:Barrios Cabrera
title:Auxiliar Informatica
department:Informatica PC
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Monitoreo
	Grupo:Proactif Care
	Grupo:Ssl vpn PC
	Grupo:Internet full
	Grupo:Grupo Baudelet
	Grupo:Informatica - Proactif Care
	Grupo:gs_invitados
	Grupo:BPM - Grupo Baudelet
	Grupo:gs_proactif
	Grupo:gs_it
Mail:patricia.barrios@proactif.com.py
Cedula:EMCONTAC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5018320
PrimerNombre:Jose Daniel
Segundo Nombre:Aveiro Sanchez
title:Analista de Salarios
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:RRHH - El Mejor
	Grupo:El Mejor
	Grupo:gs_rrhhEM
Mail:jose.aveiro@elmejor.com.py
Cedula:LPMARK02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPITBACKUP02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPIT01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP00SUC02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:ComercialPC
PrimerNombre:ComercialPC
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPCC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:laplata
PrimerNombre:LaPlata
Segundo Nombre:SQL
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
	Grupo:Administradores de DHCP
	Grupo:Users
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de empresas
	Grupo:Users
	Grupo:Administradores de Hyper-V
	Grupo:Builtin
	Grupo:Administradores
	Grupo:Builtin
Mail:[]
Cedula:4968444
PrimerNombre:Ismael
Segundo Nombre:Martinez Acosta
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:gs_suc50
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:ismael.martinez@laplata.com.py
Cedula:5313879
PrimerNombre:Karina Nathalia
Segundo Nombre:Meza Carrera
title:Representante de Servicios
department:CONTACT CENTER
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Contact Center
	Grupo:gs_contactEM
	Grupo:gs_callEM
	Grupo:El Mejor
Mail:karina.meza@elmejor.com.py
Cedula:HILDA$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5255843
PrimerNombre:Eladia
Segundo Nombre:Duarte Rolon
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:eladia.duarte@elmejor.com.py
Cedula:4756089
PrimerNombre:Teodora
Segundo Nombre:Arguello
title:FISCAL
department:OPERACIONES
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Fiscales - El Mejor
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:teodora.arguello@elmejor.com.py
Cedula:LPMARK01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:lis.guerin
PrimerNombre:Lis
Segundo Nombre:Guerin Miño
title:Back Office
department:COMERCIAL
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:cambiodehorario
	Grupo:cambio de horario
	Grupo:backofficeem
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Licitaciones_EM
	Grupo:Grupo Impulsor EM
	Grupo:Comercial - El Mejor
	Grupo:El Mejor
	Grupo:gs_comercialEM
	Grupo:gs_El_Mejor
Mail:lis.guerin@elmejor.com.py
Cedula:4526396
PrimerNombre:Laura Eloisa
Segundo Nombre:Ortiz Centurion
title:Auxiliar de Selección
department:GT
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:gs_gestiontalentoEM
	Grupo:Grupo Baudelet
	Grupo:gs_invitados
	Grupo:Grupo Impulsor EM
	Grupo:Gestion de Talento
	Grupo:El Mejor
	Grupo:gs_doEM
Mail:laura.ortiz@elmejor.com.py
Cedula:4690975
PrimerNombre:Elson Mohamed
Segundo Nombre:Portelli Velazquez
title:Encargado de Marketing
department:Desarrollo Comercial
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Marketing - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_MarketingLP
Mail:mohamed.portelli@laplata.com.py
Cedula:adminbd
PrimerNombre:adminbd
Segundo Nombre:[]
title:Administrador BD
department:Tecnologías de la Información y Comunicación
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Monitoreo
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn INFRA
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_gerTecnologiaEM
	Grupo:GTIC
	Grupo:Informatica - El Mejor
	Grupo:Grupo Impulsor EM
	Grupo:Informatica
	Grupo:Gerencias - El Mejor
	Grupo:El Mejor
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
Mail:impresora@elmejor.com.py
Cedula:LPDEP01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5241306
PrimerNombre:Guillermo Osmar
Segundo Nombre:Rotela Zelaya
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:gs_suc48
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:guillermo.rotela@laplata.com.py
Cedula:4753600
PrimerNombre:Karen Paola
Segundo Nombre:Cerna Figueredo
title:Capacitadora
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:gs_operacionesEM
Mail:karen.cerna@elmejor.com.py
Cedula:4820268
PrimerNombre:Franco Adrian
Segundo Nombre:Dure Gimenez
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet basico
	Grupo:gs_suc47
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:franco.dure@laplata.com.py
Cedula:EMCOMERCB$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP20SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCSUP1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LP38SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4927793
PrimerNombre:Myrian Isabel
Segundo Nombre:Vega Borja
title:Capacitadora
department:Operaciones
company:El Mejor
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_operacionesEM
Mail:myrian.vega@elmejor.com.py
Cedula:LP35SUC02$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5194029
PrimerNombre:Hugo Alberto
Segundo Nombre:Diarte Morinigo
title:Servicio Técnico - Proactif
department:Servicio Técnico
company:Proactif Care
directReports:[]
Miembro de:
	Grupo:Proactif Care
Mail:hugo.diarte@proactif.com.py
Cedula:LPDEV$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4708272
PrimerNombre:Cesar Fernando
Segundo Nombre:Acosta Cabrera
title:Desarrollador Jr.
department:Informatica
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_informaticaLP
	Grupo:Informatica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:Informatica
	Grupo:gs_it
Mail:cesar.acosta@laplata.com.py
Cedula:5288514
PrimerNombre:Elias Valentin
Segundo Nombre:Mercado Lopez
title:Desarrollador Jr.
department:Informatica
company:La Plata S.R.L.
directReports:[]
Miembro de:
	Grupo:Ssl vpn LP
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_informaticaLP
	Grupo:Informatica - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:Informatica
	Grupo:gs_it
Mail:elias.mercado@laplata.com.py
Cedula:LPIT05$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPIT06$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:6252411
PrimerNombre:Jhonathan
Segundo Nombre:Alegre
title:Auxiliar de Salud y Seguridad Ocupacional
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:SSO RRHH -El Mejor
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_operacionesEM
	Grupo:gs_rrhhEM
Mail:jhonathan.alegre@elmejor.com.py
Cedula:5978077
PrimerNombre:Miguel Angel
Segundo Nombre:Ramirez Alvez
title:Auxiliar de Salud y Seguridad Ocupacional
department:RRHH
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:SSO RRHH -El Mejor
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:El Mejor
	Grupo:gs_operacionesEM
	Grupo:gs_rrhhEM
Mail:miguel.ramirez@elmejor.com.py
Cedula:4085291
PrimerNombre:Nayla Fabiola
Segundo Nombre:Maciel Fleitas
title:Auxiliar Administrativo
department:ADMINISTRACION
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:gs_elmejor_all
	Grupo:Internet intermedio
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Administracion - El Mejor
	Grupo:El Mejor
	Grupo:gs_administracionEM
Mail:nayla.maciel@elmejor.com.py
Cedula:CONTACTJEFE$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:4854530
PrimerNombre:Gustavo
Segundo Nombre:Ortiz
title:Coordinador de Infraestructuras y Plataformas
department:Informatica
company:EL MEJOR S.R.L.
directReports:[]
Miembro de:
	Grupo:Monitoreo
	Grupo:gs_elmejor_all
	Grupo:Ssl vpn EM
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Monitoreo Infraestructura TIC
	Grupo:GTIC
	Grupo:Informatica - El Mejor
	Grupo:Informatica
	Grupo:El Mejor
	Grupo:Organization Management
	Grupo:gs_it
	Grupo:Admins. del dominio
	Grupo:Users
	Grupo:Administradores de empresas
	Grupo:Users
	Grupo:Administradores de esquema
	Grupo:Users
	Grupo:Administradores de Hyper-V
	Grupo:Builtin
	Grupo:Administradores
	Grupo:Builtin
Mail:gustavo.ortiz@elmejor.com.py
Cedula:LP37SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:LPMARK0001$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCOPE1$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:PCOP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5210291
PrimerNombre:Walter Alem
Segundo Nombre:Balbuena Pacheco
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc44
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:walter.balbuena@laplata.com.py
Cedula:FISCALOP$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:474439
PrimerNombre:Liz Rocio
Segundo Nombre:Palacios Aquino
title:Capacitadora
department:Operaciones
company:EL MEJOR
directReports:[]
Miembro de:
	Grupo:Capacitadores - Elmejor
	Grupo:gs_elmejor_all
	Grupo:Internet basico
	Grupo:gs_capacitacionEM
	Grupo:GrupoBaudelet
	Grupo:gs_operacionesEM
Mail:liz.palacios@elmejor.com.py
Cedula:PCADM002$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:gortiz1
PrimerNombre:Gustavo
Segundo Nombre:Ortiz
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:gortiz@grupobaudelet.com
Cedula:HealthMailboxb684a60
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:HealthMailboxb684a60814a1458ab8c9ef1a67371ee5@grupobaudelet.com
Cedula:GBDBT$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:prueba
PrimerNombre:Prueba
Segundo Nombre:Prueba
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:prueba@teconviene.com.py
Cedula:5181607
PrimerNombre:Hugo Hernan
Segundo Nombre:Ferreira Silva
title:Encargado
department:Comerciales
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet basico
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:gs_suc10
	Grupo:Avisos BPM LP
	Grupo:Encargados - La Plata
	Grupo:La Plata
	Grupo:gs_encargadosLP
Mail:hugo.ferreira@laplata.com.py
Cedula:TC01SUC01$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:EMPC$
PrimerNombre:[]
Segundo Nombre:[]
title:[]
department:[]
company:[]
directReports:[]
Miembro de:
Mail:[]
Cedula:5124382
PrimerNombre:Gabriela Elizabeth
Segundo Nombre:Lugo Romero
title:Diseñador
department:Desarrollo Comercial
company:La Plata
directReports:[]
Miembro de:
	Grupo:Internet full
	Grupo:GrupoBaudelet
	Grupo:Grupo Baudelet
	Grupo:Marketing - La Plata
	Grupo:Avisos BPM LP
	Grupo:La Plata
	Grupo:gs_MarketingLP
Mail:gabriela.lugo@laplata.com.py
