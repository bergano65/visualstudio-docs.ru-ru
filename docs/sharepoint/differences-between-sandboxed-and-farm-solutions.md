---
title: "Различия между изолированными решениями и решениями фермы | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d82bc012b2be9736b83fc07f7d0a83d354dda002
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Различия между изолированными решениями и решениями фермы
  При компиляции решения SharePoint, он будет развернут на сервере SharePoint и присоединяет отладчик для отладки. Процесс, используемый для отладки решения зависит от значения свойства изолированное решение: изолированное решение или решение фермы.  
  
 Дополнительные сведения см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Решения фермы  
 Решения фермы, размещенных в рабочем процессе IIS (W3WP.exe), выполнение кода, которые могут повлиять на всю ферму. При отладке проекта SharePoint, свойства которого изолированное решение устанавливается «решение фермы» пула приложений IIS в системе перезапускается до SharePoint отзовет или развертывает компонент таким образом, чтобы освободить все файлы, заблокированные рабочим процессом IIS. Удаляется только пула приложений IIS обслуживает URL-адрес сайта проекта SharePoint.  
  
## <a name="sandboxed-solutions"></a>Изолированные решения  
 Изолированные решения, которые размещены в SharePoint пользователь кода решения рабочий процесс (SPUCWorkerProcess.exe), запустите код, который может повлиять только на коллекцию сайтов решения. Так как изолированные решения не выполняются в рабочем процессе IIS, необходимо перезапустить пул приложений IIS, ни сервер IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Присоединяет отладчик SPUCWorkerProcess процесса, которое автоматически запускает службу SPUserCodeV4 в SharePoint и элементов управления. Это необходимо для процесс SPUCWorkerProcess повторно загрузить последнюю версию решения.  
  
## <a name="either-type-of-solution"></a>Оба типа решения  
 Для обоих типов решения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также присоединяет отладчик в браузере, чтобы включить отладку клиентского скрипта. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]использует для этой цели ядро отладки скрипта. Включение отладки скриптов, необходимо изменить параметры браузера по умолчанию при появлении.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Присоединяет отладчик только W3WP или SPUCWorkerProcess процессов, запущенных на текущем узле. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]также присоединяет управляемого COM Plus и ядро отладки рабочих процессов.  
  
## <a name="see-also"></a>См. также  
 [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Построение и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md)  
  
  