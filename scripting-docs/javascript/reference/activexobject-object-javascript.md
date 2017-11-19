---
title: "Объект ActiveXObject (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ActiveXObject
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ActiveXObject object
- Automation objects, ActiveXObject objects
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77bb743aeab563f7d7711e4caa9a0fcf0b45ff58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="activexobject-object-javascript"></a>Объект ActiveXObject (JavaScript)
Активирует объект Automation и возвращает ссылку на него.  
  
 Этот объект используется только для создания экземпляров объектов автоматизации и не содержит членов.  
  
> [!WARNING]
>  Он является расширением Microsoft и поддерживается только в Internet Explorer, но не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## <a name="parameters"></a>Параметры  
 `newObj`  
 Обязательный. Имя переменной, которой назначается объект `ActiveXObject`.  
  
 `servername`  
 Обязательный. Имя приложения, предоставляющего объект.  
  
 `typename`  
 Обязательный. Тип или класс создаваемого объекта.  
  
 `location`  
 Необязательно. Имя сетевого сервера, на котором создается объект.  
  
## <a name="remarks"></a>Примечания  
 Серверы автоматизации предоставляют по крайней мере один тип объекта. Например, приложение для обработки текстов может предоставлять объект приложения, объект документа и объект панели инструментов.  
  
 Имеется возможность указывать значения `servername.typename` для хост-компьютера в разделе реестра `HKEY_CLASSES_ROOT`. Ниже приведено несколько примеров значений, которые можно встретить в реестре ( наличие зависит от установленных программ):  
  
-   Excel.Application;  
  
-   Excel.Chart;  
  
-   Scripting.FileSystemObject;  
  
-   WScript.Shell;  
  
-   Word.Document  
  
> [!IMPORTANT]
>  Объекты ActiveX могут создавать угрозу безопасности. Для использования объектов `ActiveXObject`, возможно, потребуется настроить параметры безопасности соответствующей зоны безопасности в Internet Explorer. Например, для зоны локальной интрасети обычно необходимо задать настраиваемому параметру значение "Использование элементов управления ActiveX, не помеченных как безопасные для использования".  
  
 Чтобы определить члены объекта автоматизации, можно использовать в коде, может потребоваться использовать обозреватель объектов COM, такие как [просмотра объектов OLE/COM](http://msdn.microsoft.com/library/d0kh9f4c.aspx), если справочной документации не доступен для объекта автоматизации.  
  
 Для создания объекта автоматизации присвойте переменной объекта новое значение `ActiveXObject`:  
  
```JavaScript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 Этот код запускает приложение, создающее объект (в этом случае лист Microsoft Excel). После того как объект создан, можно ссылаться на него в коде, используя заданную переменную объекта. В следующем примере осуществляется доступ к свойствам и методам нового объекта с помощью переменной объекта `ExcelSheet` и других объектов Excel, в том числе объекта Application и коллекции ActiveSheet.Cells.  
  
```JavaScript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## <a name="requirements"></a>Требования  
 Поддерживается в следующих режимах документов: случайный режим, стандартный режим Internet Explorer 6, стандартный режим Internet Explorer 7, стандартный режим Internet Explorer 8, стандартный режим Internet Explorer 9, стандартный режим Internet Explorer 10, стандартный режим Internet Explorer 11. Не поддерживается в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] . См. [Сведения о версии](../../javascript/reference/javascript-version-information.md).  
  
> [!NOTE]
>  Создание объекта `ActiveXObject` на удаленном сервере не поддерживается в [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] и более поздних версий.  
  
## <a name="see-also"></a>См. также  
 [Функция GetObject](../../javascript/reference/getobject-function-javascript.md)   
 [Уникальный проверки подлинности с помощью Magic HTML5/WCF примера приложения](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)