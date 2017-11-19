---
title: "Объект WinRTError (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- WinRTError object [JavaScript]
- JavaScript, WinRTError object
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11b339b4fc3c4bd4f34416ffd98b8f9c3f288f98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="winrterror-object-javascript"></a>Объект WinRTError (JavaScript)
Если вызов среды выполнения Windows возвращает ошибку HRESULT, указывающую на сбой, JavaScript преобразует ее в специальную ошибку среды выполнения Windows. Объект доступен только в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], если доступна среда выполнения Windows, в составе глобального пространства имен JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
errorObj = new WinRTError();  
  
```  
  
## <a name="remarks"></a>Примечания  
 Тип ошибки WinRTError используется только для ошибок, возникающих в API среды выполнения Windows.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример возникновения и перехвата ошибки WinRTError.  
  
```JavaScript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## <a name="methods"></a>Методы  
 У объекта WinRTError нет методов.  
  
## <a name="properties"></a>Свойства  
 Те же свойства, что у объекта WinRTError [объекта Error](../../javascript/reference/error-object-javascript.md) объекта.  
  
## <a name="requirements"></a>Требования  
 Объект WinRTError поддерживается только в приложениях [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], но не в Internet Explorer.  
  
## <a name="see-also"></a>См. также  
 [Объект Error](../../javascript/reference/error-object-javascript.md)