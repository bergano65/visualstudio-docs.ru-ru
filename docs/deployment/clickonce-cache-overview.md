---
title: "Общие сведения о кэше ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "приложения ClickOnce, кэш"
  - "развертывание ClickOnce, кэш"
  - "приложения Windows, развертывание ClickOnce"
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Общие сведения о кэше ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Все приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], установлены ли они локально или размещаются в сети, хранятся на клиентском компьютере в *кэше* приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Кэш [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] — это семейство скрытых подкаталогов в каталоге "Локальные параметры" папки "Documents and Settings" текущего пользователя.  В этом кэше содержатся все файлы приложения, включая сборки, файлы конфигурации, параметры приложения и пользовательские настройки, а также каталог данных.  Кэш также отвечает за миграцию каталога данных приложения при переходе на более позднюю версию.  Дополнительные сведения о миграции данных см. в разделе [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Предоставляя одно местоположение для хранилища приложения, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] берет на себя выполнение задачи управления физической установкой приложения вместо пользователя.  Кэш также помогает изолировать приложения путем хранения сборок и файлов данных для всех приложений и их разных версий отдельно друг от друга.  Например, при обновлении приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] эта версия и ее информационные ресурсы предоставляются с их собственными каталогами в кэше.  
  
## Квота хранилища кэша  
 Приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], размещаемые в сети, ограничиваются по объему занимаемого ими места квотой, лимитирующей размер кэша [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Размер кэша применяется ко всем интерактивным приложениям пользователя; одиночное интерактивное приложение с частичным доверием может занимать не более половины пространства квоты.  Установленные приложения не ограничиваются размером квоты и не учитываются в предельном размере кэша.  Для всех приложений [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] кэше сохраняются только текущая версия и ранее установленная версия.  
  
 По умолчанию на клиентских компьютерах имеется 250 МБ хранилища для интерактивных приложений [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  В этом пределе не учитываются файлы данных.  Администратор системы может увеличить или уменьшить данную квоту на конкретном клиентском компьютере, изменив значение раздела реестра, HKEY\_CURRENT\_USER\\Software\\Classes\\Software\\Microsoft\\Windows\\CurrentVersion\\Deployment\\OnlineAppQuotaInKB, которое представлено значением DWORD, выражающим размер кэша в килобайтах.  Например, чтобы уменьшить размер кэша до 50 МБ, это значение следовало бы установить равным 51200.  
  
## См. также  
 [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)