---
title: Идебугпоинтерфиелд | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d92b1b4d6efda1b8f05c594368a05bd833c9f34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705828"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет тип указателя.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик символов реализует этот интерфейс для представления указателя.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) для получения этого интерфейса из интерфейса [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , если метод [Kind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращает `FIELD_TYPE_POINTER` .  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
 Помимо методов в `IDebugField` `IDebugContainerField` интерфейсах и, этот интерфейс реализует следующий метод:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Возвращает [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , описывающий цель указателя.|  
  
## <a name="remarks"></a>Remarks  
 В C/C++ указатель может быть контейнером, если он используется с нотацией массива. Например, `char *pString` `pString` имеет тип указателя на `char` . `pString[3]` имеет тип контейнера, который является указателем на `char` , ссылающийся на четвертый элемент этого контейнера.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
