---
title: IDebugGenericFieldDefinition | Документация Майкрософт
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
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ff8e44a7963aab80a1f2947fe9a34532a0b7e725
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570706"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugGenericFieldDefinition](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebuggenericfielddefinition).  
  
Представляет определение поля для универсального типа управляемого кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## <a name="methods"></a>Методы  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Создает экземпляр поля задан массив аргументов типа.|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Получает параметры типа, учитывая количество параметров.|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Возвращает число параметров типа, связанное с этим универсальным.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

