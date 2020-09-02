---
title: Реализация поставщика порта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152675"
---
# <a name="implementing-a-port-supplier"></a>Реализация поставщика порта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Поставщик порта предоставляет порты по запросу к диспетчеру отладки сеансов (SDM). Поставщик порта должен быть реализован при отладке на компьютере, отличном от DCOM, или при необходимости поддержки нового устройства. Например, чтобы обеспечить отладку на мобильном телефоне, можно реализовать поставщика порта, который предоставляет порты, подключающиеся к сотовому телефону (возможно, с помощью ИНФРАКРАСного соединения или подключения к ячейке), и перечисляет процессы и программы, запущенные на телефоне.  
  
 Для отладки программ на компьютерах под управлением Windows (включая удаленную отладку) Visual Studio предоставляет поставщики портов для процессов машинного кода и среды CLR, поэтому в таких случаях нет необходимости реализовывать собственный поставщик порта.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Реализация и регистрация поставщика порта](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Описывает взаимодействие SDM с поставщиком порта и его портами.  
  
 [Интерфейс поставщика необходимого порта](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Документирует интерфейсы, которые должны быть реализованы для получения поставщика порта.  
  
## <a name="related-sections"></a>См. также  
 [Отладчик: основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные понятия архитектуры отладки.  
  
## <a name="see-also"></a>См. также:  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
