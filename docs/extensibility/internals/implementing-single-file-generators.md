---
title: Реализация генераторов с одним файлом | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727180"
---
# <a name="implementing-single-file-generators"></a>Реализация генераторов одного файла
Пользовательский инструмент (иногда называемый генератором одиночных файлов) можно использовать для расширения [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] систем проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Пользовательский инструмент — это COM-компонент, реализующий интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. С помощью этого интерфейса пользовательское средство преобразует один входной файл в отдельный выходной файл. Результатом преобразования может быть исходный код или любые другие полезные выходные данные. Два примера пользовательских файлов кода — это код, создаваемый в ответ на изменения в визуальном конструкторе и файлах, созданных с помощью языка описания веб-служб (WSDL).

 При загрузке пользовательского инструмента или сохранении входного файла система проекта вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> и передает ссылку на <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> интерфейс обратного вызова, при котором средство может сообщить пользователю о ходе выполнения.

 Выходной файл, формируемый настраиваемым инструментом, добавляется в проект с зависимостью от входного файла. Система проекта автоматически определяет имя выходного файла на основе строки, возвращаемой реализацией <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> в пользовательском средстве.

 Пользовательский инструмент должен реализовывать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. При необходимости пользовательские инструменты поддерживают интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> для получения сведений из источников, отличных от входного файла. В любом случае, прежде чем можно будет использовать пользовательский инструмент, необходимо зарегистрировать его в системе или в локальном реестре [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения о регистрации пользовательских средств см. в разделе [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>См. также
- [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)