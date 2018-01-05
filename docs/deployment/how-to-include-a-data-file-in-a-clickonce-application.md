---
title: "Как: включение файла данных в приложение ClickOnce | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "15"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: a7ddfdb0518a8e3154d966fdea884bf7f2e3ea37
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>How to: Include a Data File in a ClickOnce Application
Каждый [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установки приложения назначается каталог данных на локальном диске конечного компьютера где приложение может работать со своими данными. Файлы данных могут содержать файлы любого типа: текстовые файлы, XML-файлы или даже файлы Microsoft Access (.mdb) базы данных. Следующие процедуры показывают, как добавить файл данных любого типа в вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Чтобы включить файл данных с помощью Mage.exe  
  
1.  Добавьте в файл данных в каталог приложения с остальными файлами приложения.  
  
     Как правило, каталог приложения будет каталог меток, относящихся к текущей версии развертывания — например, v1.0.0.0.  
  
2.  Обновите манифест приложения в список файла данных.  
  
     **Mage: -u v1.0.0.0\Application.manifest - FromDirectory v1.0.0.0**  
  
     Эта задача выполняется повторно создает список файлов в манифесте приложения, а также автоматически генерируются хэш-подписи.  
  
3.  Откройте манифест приложения в предпочтительном текстовом или XML-редакторе и найдите `file` элемент для недавно добавленного файла.  
  
     Если вы добавили в XML-файл с именем `Data.xml`, файл будет выглядеть примерно в следующем примере кода.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Добавьте атрибут `type` к данному элементу и передайте в него значение `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Повторно подписать манифест приложения, используя пару ключей или сертификат и повторно подпишите манифест развертывания.  
  
     Манифест развертывания необходимо подписать повторно из-за изменения ее хэш-код манифеста приложения.  
  
     **манифест приложения -s Mage - cf cert_file - pwd пароль**  
  
     **-u развертывания Mage манифеста - appm-манифест приложения**  
  
     **манифест развертывания -s Mage - cf certfile - pwd пароль**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Чтобы включить файл данных с помощью MageUI.exe  
  
1.  Добавьте в файл данных в каталог приложения с остальными файлами приложения.  
  
2.  Как правило, каталог приложения будет каталог меток, относящихся к текущей версии развертывания — например, v1.0.0.0.  
  
3.  На **файл** меню, нажмите кнопку **откройте** открыть манифест приложения.  
  
4.  Выберите **файлы** вкладки.  
  
5.  В текстовом поле в верхней части вкладки, введите в каталог, содержащий файлы приложения и нажмите кнопку **заполнить**.  
  
     Файл данных будет отображаться в сетке.  
  
6.  Задать **тип файла** значение из файла данных для **данные**.  
  
7.  Сохраните манифест приложения и повторной подписи файла.  
  
     MageUI.exe выводит приглашение для повторной подписи файла.  
  
8.  Повторно подпишите манифест развертывания  
  
     Манифест развертывания необходимо подписать повторно из-за изменения ее хэш-код манифеста приложения.  
  
## <a name="see-also"></a>См. также  
 [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)