---
title: С помощью диспетчера текстов для наблюдения за глобальные параметры | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 494e61c7239eb2caacd3facdddbe2cd26b3d0a73
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336980"
---
# <a name="use-the-text-manager-to-monitor-global-settings"></a>Использование диспетчера текстов для наблюдения за глобальные параметры
Если реализовать базовый редактор, необходимо отслеживать изменения, сделанные глобальные параметры, так как эти изменения могут повлиять на ваш экземпляр редактора. Можно отслеживать изменения путем прослушивания события, вызванные диспетчера текстов. Например при указании глобальных предпочтение внешний вид или поведение компонента в базовом редакторе, например его объект данных документа, диспетчер текстовых сохраняет эти данные и передает их все затронутые этой проблемой клиенты.

## <a name="text-manager-functions"></a>Текстовые функции manager
 Диспетчер текста вызывает события для ряда параметров, включая следующие:

- Является ли буфер в систему управления версиями

- Регистрация для уведомления об изменении файла

- Как для отслеживания какие представления связаны с определенным буферов

- Предпочтения цветовое выделение текста

- Вкладки и место установки

  Параметры, которые уникальны для данного языка не находятся под управлением диспетчера текстов. Эти параметры должны управляться каждая языковая служба.

  Уведомление о событии для диспетчера текстов обеспечивается <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> интерфейс. Этот интерфейс реализуется на клиенте для обработки событий вызвал диспетчера текстов. Регистрация для этих событий с помощью <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> интерфейс в диспетчере текста.

## <a name="see-also"></a>См. также
- [В редакторе](../extensibility/inside-the-core-editor.md)
- [Возможности редактора](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198)