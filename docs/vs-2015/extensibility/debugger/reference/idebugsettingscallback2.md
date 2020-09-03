---
title: IDebugSettingsCallback2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2 interface
ms.assetid: 7e525d0b-7d7a-4d1c-8b78-e1398fa922f2
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c3e962c00d6c9230cab765ed56e7607cbfd91765
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153141"
---
# <a name="idebugsettingscallback2"></a>IDebugSettingsCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Включает модули отладки для удаленного считывания параметров метрик.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugSettingsCallback2D : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется обратным вызовом события диспетчером отладки сеанса и используется механизмами отладки. Его также можно использовать локально вместо Дбгметрик [d]. lib.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugSettingsCallback2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[EnumEEs](../../../extensibility/debugger/reference/idebugsettingscallback2-enumees.md)|Перечисляет доступные средства оценки выражений по идентификаторам языка и поставщика.|  
|[GetEELocalObject](../../../extensibility/debugger/reference/idebugsettingscallback2-geteelocalobject.md)|Извлекает локальный объект средства оценки выражений, заданный метрикой.|  
|[GetEEMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricdword.md)|Извлекает значение, соответствующее заданной метрике средства оценки выражений.|  
|[GetEEMetricFile](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricfile.md)|Извлекает файл метрики средства оценки выражений по заданному имени или метрике.|  
|[GetEEMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricguid.md)|Возвращает уникальный идентификатор для метрики средства оценки выражений по заданному имени.|  
|[GetEEMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-geteemetricstring.md)|Получает строку значений метрики средства оценки выражений по его имени.|  
|[GetMetricDword](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricdword.md)|Извлекает значение метрики по ее имени.|  
|[GetMetricGuid](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricguid.md)|Извлекает уникальный идентификатор метрики по ее имени.|  
|[GetMetricString](../../../extensibility/debugger/reference/idebugsettingscallback2-getmetricstring.md)|Возвращает строку значения метрики, заданную ее именем.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Пример  
 В следующем примере показана функция, которая принимает объект **IDebugSettingsCallback2** в качестве параметра.  
  
```cpp#  
HRESULT GetDebugSettingsCallback (IDebugSettingsCallback2 **ppCallback)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppCallback )  
   {  
        if ( EVAL(m_pdec) )  
            hRes = m_pdec->QueryInterface(IID_IDebugSettingsCallback2, (void **)ppCallback);  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```
