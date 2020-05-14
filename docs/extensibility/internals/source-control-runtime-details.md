---
title: Источник управления Runtime Подробная информация (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705040"
---
# <a name="source-control-runtime-details"></a>Сведения о среде выполнения системы управления версиями
Проект добавляется в элемент управления исходным элементом, когда пользователь добавляет файл в проекте в элемент управления исходным элементом или через контроллер автоматизации, например мастер. Проект не указывает для себя, что он находится под контролем источника; он поддерживает элемент управления исходным источником, но должен быть добавлен к нему вручную.

## <a name="registering-with-a-source-control-package"></a>Регистрация с пакетом управления исходным ресурсом
 При добавлении файла в проекте в <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> элемент управления исходным ресурсом среда требует предоставить вам четыре непрозрачные строки, которые используются в качестве файлов cookie системой управления исходным источником. Храните эти строки в файле проекта. Эти строки должны быть переданы в заглушку управления исходным элементом (компонент Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>управляющий пакетами управления исходным управлением) при запуске типа проекта, вызывая вызов. Это, в свою очередь, загружает соответствующий пакет `IVsSccManager2::RegisterSccProject`управления исходным источником и направляет вызов на его реализацию.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
