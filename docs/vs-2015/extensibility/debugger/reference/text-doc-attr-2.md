---
title: TEXT_DOC_ATTR_2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 761c94673a5f5cec55ce0174561946f1d5302cb4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993513"
---
# <a name="textdocattr2"></a>TEXT_DOC_ATTR_2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает атрибуты документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef DWORD TEXT_DOC_ATTR_2;  
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
```csharp  
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
## <a name="members"></a>Участники  
 TEXT_DOC_ATTR_READONLY_2  
 Указывает, что документ доступен только для чтения.  
  
## <a name="remarks"></a>Примечания  
  
> [!NOTE]
>  Это значение фактически не определен в сборке для C#. Вместо этого необходимо скопировать определение в файле исходного кода.  
  
 Передается в качестве аргумента для [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) метод.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)
