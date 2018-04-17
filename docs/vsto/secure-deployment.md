---
title: Безопасное развертывание | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1efc8087476cbe879a647288c35a7e7f329100a7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="secure-deployment"></a>Безопасное развертывание
  При создании решения Office, на компьютере разработчика обновляется автоматически, чтобы код в проекте для запуска. Тем не менее, при развертывании решения необходимо предоставить свидетельство, на котором будет основываться решение о доверии подписи решения с сертификатом или с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] ключ запроса доверия. Дополнительные сведения см. в разделе [Присвоение уровня доверия решениям Office](../vsto/granting-trust-to-office-solutions.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Для настроек на уровне документа при развертывании документа в сетевую папку, необходимо также добавить расположение документа в список надежных расположений в центре управления безопасностью приложения Office. Дополнительные сведения об установке разрешений документа компьютеры конечных пользователей см. в разделе [Присвоение уровня доверия документам](../vsto/granting-trust-to-documents.md).  
  
## <a name="preventing-office-solutions-from-running-code"></a>Препятствует выполнению кода, решения Office  
 Администраторы могут использовать реестр для предотвращения выполнения на компьютере всех решений Office. Если решения Office, имеющая расширения управляемого кода открыт, Visual Studio Tools для Office среда выполнения проверяет ли запись с именем `Disabled` существует в одном из следующих разделов реестра на компьютере:  
  
-   `HKEY_CURRENT_USER\Software\Microsoft\VSTO`  
  
-   `HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO`  
  
 Чтобы предотвратить выполнение кода решения Office, создайте `Disabled` входа в одном или обоих этих разделов реестра и укажите один из следующих типов данных и значения для `Disabled`:  
  
-   Значения типа REG_SZ или REG_EXPAND_SZ, настроенного для любой строки, отличные от «0» (нуль).  
  
-   REG_DWORD, которой присваивается значение, отличное от 0 (ноль).  
  
 Чтобы включить решений Office для выполнения кода, задайте оба `Disabled` записи значение 0 (ноль), или удалить записи реестра.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Подготовка компьютеров для выполнения или размещения решений Office](http://msdn.microsoft.com/en-us/be1b173f-7261-4d74-aa4e-94ccd43db8d8)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)  
  
  