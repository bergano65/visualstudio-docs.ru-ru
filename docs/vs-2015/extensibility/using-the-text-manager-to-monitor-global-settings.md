---
title: С помощью диспетчера текстов для наблюдения за глобальные параметры | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 792c566eda53cb8a4703e8ab03982952c518d8e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980229"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>С помощью диспетчера текстов для наблюдения за глобальные параметры
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если реализовать базовый редактор, необходимо отслеживать изменения, сделанные глобальные параметры, так как эти изменения могут повлиять на ваш экземпляр редактора. Можно отслеживать изменения путем прослушивания события, вызванные диспетчера текстов. Например при указании глобальных предпочтение внешний вид или поведение компонента в базовом редакторе, например его объект данных документа, диспетчер текстовых сохраняет эти данные и передает их все затронутые этой проблемой клиенты.  
  
## <a name="text-manager-functions"></a>Функции диспетчера текстов  
 Диспетчер текста вызывает события для ряда параметров, включая следующие:  
  
- Является ли буфер в систему управления версиями  
  
- Регистрация для уведомления об изменении файла  
  
- Как для отслеживания какие представления связаны с определенным буферов  
  
- Предпочтения цветовое выделение текста  
  
- Вкладки и место установки  
  
  Параметры, которые уникальны для данного языка не находятся под управлением диспетчера текстов. Эти параметры должны управляться каждая языковая служба.  
  
  Уведомление о событии для диспетчера текстов обеспечивается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> интерфейс. Этот интерфейс реализуется на клиенте для обработки событий вызвал диспетчера текстов. Регистрация для этих событий с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> интерфейс в диспетчере текста.  
  
## <a name="see-also"></a>См. также  
 [В редакторе](../extensibility/inside-the-core-editor.md)   
 [Возможности редактора](http://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
