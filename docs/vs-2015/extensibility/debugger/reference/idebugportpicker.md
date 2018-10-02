---
title: IDebugPortPicker | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b92f188dd2bed678e4117adde7c61d8844e8360
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569416"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugPortPicker](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker).  
  
Представляет настраиваемый пользовательский Интерфейс для выбора порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется поставщикам портов. Поставщика порта определяет их выбора порта предоставлением в качестве идентификатора класса CLSID, и выберите пункт `metricPortPickerCLSID` метрик в предоставленный идентификатор CLSID.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugPortPicker`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Отображает указанный диалоговое окно, которое позволяет пользователю выбрать порт.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Задает поставщик службы.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

