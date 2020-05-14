---
title: Внедрение однофайловых генераторов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707659"
---
# <a name="implementing-single-file-generators"></a>Реализация генераторов одного файла
Пользовательский инструмент - иногда называют как единый генератор файлов [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] может [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]быть использован для расширения и проектных систем в . Пользовательский инструмент — это компонент <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> COM, который реализует интерфейс. Используя этот интерфейс, пользовательский инструмент преобразует один файл ввода в единый выводный файл. Результатом преобразования может быть исходный код или любой другой полезный выход. Двумя примерами пользовательских файлов кода, генерируемых на заказ, являются код, генерируемый в ответ на изменения в визуальном конструкторе, и файлы, генерируемые с помощью языка описания веб-служб (WSDL).

 При загрузке пользовательского инструмента или сохранении файла ввода <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> проектная система вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> и передает ссылку на интерфейс обратного вызова, в результате чего инструмент может сообщить пользователю о своем прогрессе.

 Выводной файл, генерируемый пользовательским инструментом, добавляется в проект с зависимостью от файла ввода. Проектная система автоматически определяет имя выходного файла на основе строки, возвращенной реализацией <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>пользовательского инструмента.

 Пользовательский инструмент должен <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> реализовать интерфейс. Дополнительно пользовательские инструменты <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> поддерживают интерфейс для получения информации из других источников, кроме файла ввода. В любом случае, прежде чем вы сможете использовать пользовательский инструмент, вы должны зарегистрировать его в системе или в местном реестре. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Для получения дополнительной информации о регистрации пользовательских инструментов, см [Регистрация генераторов единого файла](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>См. также
- [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)
