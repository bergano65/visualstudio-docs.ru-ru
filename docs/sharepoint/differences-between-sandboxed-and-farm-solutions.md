---
title: "Различия между изолированными решениями и решениями фермы"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "решения фермы [разработка приложений SharePoint в Visual Studio]"
  - "изолированные решения [разработка приложений SharePoint в Visual Studio]"
  - "разработка приложений SharePoint в Visual Studio, решения фермы"
  - "разработка приложений SharePoint в Visual Studio, изолированные решения"
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Различия между изолированными решениями и решениями фермы
  При компиляции решение SharePoint развертывается на сервере SharePoint. К нему присоединяется отладчик для выполнения отладки.  Процесс, используемый для отладки решения, зависит от значения свойства "Изолированное решение": изолированное решение или решение фермы.  
  
 Для получения дополнительной информации см. [Замечания об обезвреженных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
## Решения фермы  
 В решениях фермы, размещенных в рабочем процессе IIS \(W3WP.exe\), выполняется код, который может повлиять на всю ферму.  При отладке проекта SharePoint, в качестве значения свойства "Изолированное решение" которого задано "решение фермы", перед тем, как SharePoint отзовет или развернет компонент, выполняется повторный запуск пула приложений IIS для разблокирования всех файлов, заблокированных рабочим процессом IIS.  Повторный запуск выполняется только для пула приложений IIS, обслуживающего URL\-адрес сайта проекта SharePoint.  
  
## Изолированные решения  
 В изолированных решениях, размещенных в рабочем процессе решения кода пользователя SharePoint \(SPUCWorkerProcess.exe\), выполняется код, который может повлиять только на коллекцию сайтов решения.  Поскольку изолированные решения не выполняются в рабочем процессе IIS, не нужно перезапускать ни пул приложений IIS, ни сервер IIS.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] присоединяет к процессу SPUCWorkerProcess отладчик, который автоматически переключается и управляется службой SPUserCodeV4 в SharePoint.  Для загрузки последней версии решения запускать процесс SPUCWorkerProcess повторно не обязательно.  
  
## Оба типа решения  
 Для обоих типов решения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также присоединяет к браузеру отладчик, что позволяет выполнять отладку скрипта на стороне клиента.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] использует для этой цели ядро отладки скрипта.  Чтобы включить отладку скрипта, нужно изменить параметры браузера по умолчанию при получении соответствующего запроса.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] присоединяет отладчик только к процессам W3WP или SPUCWorkerProcess, в которых выполняется текущий сайт.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также присоединяет модель управляемого кода COM Plus и ядро отладки рабочих процессов.  
  
## См. также  
 [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Построение и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Замечания об обезвреженных решениях](../sharepoint/sandboxed-solution-considerations.md)  
  
  