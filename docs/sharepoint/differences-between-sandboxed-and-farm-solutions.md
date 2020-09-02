---
title: Различия между песочницами и решениями фермы | Документация Майкрософт
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 073e62b473ebfcec5f71ae1907e8f9e385333411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967550"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Различия между песочницами и решениями фермы
  При компиляции решения SharePoint оно развертывается на сервере SharePoint, а отладчик подключается для его отладки. Процесс, используемый для отладки решения, зависит от параметра свойства изолированного решения: изолированное решение или решение фермы.

 Дополнительные сведения см. в статье [рекомендации по изолированным решениям](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Решения фермы
 Решения фермы, размещенные в рабочем процессе IIS (W3WP.exe), выполняют код, который может повлиять на всю ферму. При отладке проекта SharePoint, для свойства изолированного решения которого задано значение "решение фермы", пул приложений IIS системы перезапускается до того, как SharePoint отменяет или развертывает функцию, чтобы освободить все файлы, заблокированные рабочим процессом IIS. Только пул приложений IIS, обслуживающий URL-адрес сайта проекта SharePoint, перезапускается.

## <a name="sandboxed-solutions"></a>Изолированные решения
 Изолированные решения, которые размещаются в рабочем процессе решения пользовательского кода SharePoint (SPUCWorkerProcess.exe), выполняют код, который может повлиять только на семейство веб-сайтов решения. Поскольку изолированные решения не выполняются в рабочем процессе IIS, не нужно перезапускать ни пул приложений IIS, ни сервер IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] присоединяет отладчик к процессу Спукворкерпроцесс, который служба SPUserCodeV4 в SharePoint автоматически активирует и контролирует. В процессе Спукворкерпроцесс не требуется перезапускать для загрузки последней версии решения.

## <a name="either-type-of-solution"></a>Любой тип решения
 При использовании любого типа решения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также подключает отладчик к браузеру для включения отладки скриптов на стороне клиента. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] для этой цели использует обработчик отладки скриптов. Чтобы включить отладку скриптов, необходимо изменить параметры браузера по умолчанию при появлении соответствующего запроса.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Подключает отладчик только к процессам W3WP или Спукворкерпроцесс, выполняющим текущий сайт. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также присоединяет управляемые обработчики COM Plus и отладки рабочих процессов.

## <a name="see-also"></a>См. также раздел
- [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md)
- [Сборка и отладка решений SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Рекомендации по изолированным решениям](../sharepoint/sandboxed-solution-considerations.md)
