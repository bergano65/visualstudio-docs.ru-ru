---
title: IDebugProgramProvider2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2
helpviewer_keywords:
- IDebugProgramProvider2 interface
ms.assetid: a9ec7b3e-a59c-4069-b2ee-6f45916eeb78
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a3ccac5dc60c10983d3b1a33978196fad5197d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146322"
---
# <a name="idebugprogramprovider2"></a>IDebugProgramProvider2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот зарегистрированный интерфейс позволяет диспетчеру отладки сеансов (SDM) получать сведения о программах, опубликованных через интерфейс [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgramProvider2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для предоставления сведений о отлаживаемой программе. Этот интерфейс регистрируется в разделе DE реестра с использованием метрики `metricProgramProvider` , как описано в [вспомогательных средствах SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите `CoCreateInstance` функцию COM с помощью `CLSID` поставщика программы, полученного из реестра. См. пример.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)|Получение сведений о выполняющихся и фильтруемых программах различными способами.|  
|[GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)|Возвращает узел программы по указанному ИДЕНТИФИКАТОРу процесса.|  
|[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)|Устанавливает обратный вызов для отслеживания событий поставщика, связанных с определенными видами процессов.|  
|[Pragma](../../../extensibility/debugger/reference/idebugprogramprovider2-setlocale.md)|Устанавливает языковой стандарт для всех зависящих от языка ресурсов, необходимых для DE.|  
  
## <a name="remarks"></a>Remarks  
 Как правило, процесс использует этот интерфейс, чтобы узнать о программах, выполняющихся в этом процессе.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Пример  
  
```cpp#  
IDebugProgramProvider2 *GetProgramProvider(GUID *pDebugEngineGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugProgramProvider2 *pProvider = NULL;  
    if (pDebugEngineGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetMetric(NULL,  
                    metrictypeEngine,  
                    *pDebugEngineGuid,  
                    metricProgramProvider,  
                    &clsidProvider,  
                    strRegistrationRoot);  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugProgramProvider2> spProgramProvider;  
            spProgramProvider.CoCreateInstance(clsidProvider);  
            if (spProgramProvider != NULL) {  
                pProvider = spProgramProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
