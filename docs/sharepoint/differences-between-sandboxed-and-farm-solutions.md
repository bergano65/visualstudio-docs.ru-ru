---
title: Различия между изолированными решениями и решениями фермы | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f4f37d908448eba54924589cd669dbdda84956d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849752"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Различия между изолированными решениями и решениями фермы
  При компиляции решения SharePoint, он будет развернут на сервере SharePoint, и отладчик подключается к его отладки. Процесс, используемый для отладки решения зависит от значения свойства изолированное решение: изолированное решение или решение фермы.  
  
 Дополнительные сведения см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Решения фермы
 Решения для фермы, которые размещаются в рабочий процесс IIS (W3WP.exe), выполнение кода, которые могут повлиять на всю ферму. При отладке проекта SharePoint, свойство которого изолированное решение имеет значение «решение фермы» пула приложений IIS системы перезапускается до SharePoint отзовет или развертывает компонент таким образом, чтобы освободить все файлы, заблокированные рабочим процессом IIS. Только пула приложений IIS обслуживает URL-адрес сайта проекта SharePoint используется повторно.  
  
## <a name="sandboxed-solutions"></a>Изолированные решения
 Изолированные решения, которые размещены в SharePoint пользователь код решения рабочий процесс (SPUCWorkerProcess.exe), запустите код, который может повлиять только на коллекцию сайтов решения. Так как изолированные решения не выполняются в рабочем процессе IIS, необходимо перезапустить пул приложений IIS, ни сервер IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Присоединяет отладчик к процессу SPUCWorkerProcess, которое автоматически запускает службу SPUserCodeV4 в SharePoint и элементов управления. Это необходимо для процесс SPUCWorkerProcess повторно загрузить последнюю версию решения.  
  
## <a name="either-type-of-solution"></a>Оба типа решения
 Для обоих типов решения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также присоединяет отладчик в браузере, чтобы включить отладку клиентского скрипта. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] использует для этой цели ядро отладки скрипта. Включение отладки скриптов, необходимо изменить параметры браузера по умолчанию при появлении запроса.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Присоединяет отладчик только W3WP или SPUCWorkerProcess процессов, запущенных на текущем узле. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Кроме того, присоединяет управляемого кода COM Plus и ядро отладки рабочих процессов.  
  
## <a name="see-also"></a>См. также
 [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Построение и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md)  
