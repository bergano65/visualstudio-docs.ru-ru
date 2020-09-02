---
title: Модули | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a2b2f04e1088b9b06cb05015a6b0b4da5d60927
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153750"
---
# <a name="modules"></a>Модули
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В плане архитектуры отладчика это **модуль**:  
  
- — Это физический контейнер кода, например исполняемый файл или библиотека DLL.  
  
- Может перезагружать свои символы и описывать саму себя. Описания модулей отображаются в окне Модули интегрированной среды разработки.  
  
- Представляется интерфейсом [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , созданным модулем отладки для описания модуля.  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия отладчика](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
