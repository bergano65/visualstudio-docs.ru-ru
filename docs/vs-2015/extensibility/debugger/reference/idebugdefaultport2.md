---
title: IDebugDefaultPort2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca0b6b7e9753b346b8a995ffd8ddcb6cc53fe7c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697518"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет несколько методов для доступа к серверу и средствам уведомления на порту.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс, чтобы представить порт отладки для доступа к программам. Пользовательский поставщик порта также может реализовать этот интерфейс, если он обрабатывает удаленную отладку.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс предоставляет аргумент для методов в интерфейсе [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Вызов [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) в интерфейсе [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) также может получить этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
 В дополнение к методам, определенным в [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Получает интерфейс уведомления порта от этого порта.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Возвращает интерфейс для сервера, на котором размещен этот порт.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Определяет, работает ли этот порт на локальном компьютере.|  
  
## <a name="remarks"></a>Remarks  
 Имя " `IDebugDefaultPort2` " является битом атрибутаDurableService, так как оно не представляет порт по умолчанию. Его можно назвать «IDebugPort3».  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
