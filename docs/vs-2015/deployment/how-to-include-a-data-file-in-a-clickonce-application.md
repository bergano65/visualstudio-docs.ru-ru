---
title: 'Практическое: Include a Data File in a ClickOnce Application | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ee465b3b4524b4f5c530369722f8bdaf36b85227
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572814"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>How to: Include a Data File in a ClickOnce Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: включение файла данных в приложении ClickOnce](https://docs.microsoft.com/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).  
  
Каждый [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение, которое установить назначается каталог данных на локальном диске конечного компьютера где приложения могут управлять собственными данными. Файлы данных могут содержать файлы любого типа: текстовые файлы, XML-файлы или даже файлы Microsoft Access (MDB-файл). Ниже показано, как добавить файл данных любого типа в вашей [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Чтобы включить файл данных с помощью Mage.exe  
  
1.  Добавьте в файл данных в каталог приложения с остальными файлами приложения.  
  
     Как правило, каталог приложения будет каталог с текущей версии развертывания, например, v1.0.0.0.  
  
2.  Обновите манифест приложения в список файла данных.  
  
     **v1.0.0.0 - FromDirectory v1.0.0.0\Application.manifest -u Mage**  
  
     Для выполнения этой задачи повторно создает список файлов в манифесте приложения, а также автоматически создает хэш-подписи.  
  
3.  Откройте манифест приложения в любом текстовом или редакторе XML и найдите `file` элемент для недавно добавленного файла.  
  
     Если вы добавили XML-файл с именем `Data.xml`, файл будет выглядеть аналогично в следующем примере кода.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Добавьте атрибут `type` данного элемента и задать в нем значение `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Повторно подписать манифест приложения, используя пару ключей или сертификат и затем снова подписать манифест развертывания.  
  
     Необходимо повторно подписать манифест развертывания из-за изменения ее хэш-код манифеста приложения.  
  
     **манифест приложения -s Mage - cf cert_file - pwd пароль**  
  
     **-u развертывания Mage манифеста - appm-манифест приложения**  
  
     **манифест развертывания -s Mage - cf certfile - pwd пароль**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Чтобы включить файл данных с помощью MageUI.exe  
  
1.  Добавьте в файл данных в каталог приложения с остальными файлами приложения.  
  
2.  Как правило, каталог приложения будет каталог с текущей версии развертывания, например, v1.0.0.0.  
  
3.  На **файл** меню, щелкните **откройте** открыть манифест приложения.  
  
4.  Выберите **файлы** вкладки.  
  
5.  В текстовом поле в верхней части вкладки введите каталог, содержащий файлы приложения и нажмите кнопку **заполнить**.  
  
     Файл данных будет отображаться в сетке.  
  
6.  Задайте **тип файла** значение файла данных для **данных**.  
  
7.  Сохраните манифест приложения и повторной подписи файла.  
  
     MageUI.exe предложит повторной подписи файла.  
  
8.  Повторно подпишите манифест развертывания  
  
     Необходимо повторно подписать манифест развертывания из-за изменения ее хэш-код манифеста приложения.  
  
## <a name="see-also"></a>См. также  
 [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



