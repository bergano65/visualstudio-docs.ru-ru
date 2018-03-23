---
title: Получение шрифт и цвет шрифта для текста Раскраска | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6137acabfc39914d42524ac996fb0c76a518d025
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Получение шрифт и цвет шрифта для текста выделение цветом
Процесс, который подготавливает к просмотру или отображение цветом текста в элементы пользовательского интерфейса (UI) зависит от типа проекта, технологии и разработчик предпочтений. **Шрифты и цвета** сохраняет страницу свойств параметры.

 Большинство реализаций, в которых отображаются цветом текста необходимо <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> и соответствующие интерфейсы для представления, извлечение и сохранение текста для отображения параметров.

> [!NOTE]
>  При настройке базового редактора (который поддерживает **EditorCategory текст**), рекомендуется использовать технологии выделения цветом, в службе языка. Дополнительные сведения см. в разделе [шрифт и цвет Обзор](../extensibility/font-and-color-overview.md).

## <a name="getting-default-font-and-color-information"></a>Получение стандартный шрифт и цвет шрифта
 Все **шрифты и цвета** должны быть указаны параметры окна, отображающие текст в **отображаемые элементы** одного **категории**. Дополнительные сведения см. в разделе [шрифты и цвета, среда, диалоговое окно «Параметры»](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).

Для выделения цветом, VSPackage должен получить текущий **шрифты и цвета** параметры. Пакет VSPackage можно получить текущие параметры одним из следующих способов, в зависимости от своих потребностей.

-   Используйте механизм сохранения шрифта и цвета для получения хранимой или текущего состояния. Дополнительные сведения см. в разделе [параметров доступа к хранимых шрифта и](../extensibility/accessing-stored-font-and-color-settings.md).

-   Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> интерфейс службы, который предоставляет данные шрифта и цвета для получения экземпляра <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, если пакет VSPackage не также поставщика шрифта или цвета.

-   Реализовать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.

Чтобы убедиться, что результаты, полученные путем опроса, актуальные, может оказаться полезным использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> интерфейс, чтобы определить, требуется ли обновление до вызова методов получения <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> интерфейса.

После получения информации шрифта и цвета, синтаксический анализ текста для отображения для определения элементов, требующих выделение цветом. Отображать текст с помощью соответствующих шрифтов и цветов.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>
- [Работами со шрифтами и текстом](/dotnet/framework/winforms/advanced/using-fonts-and-text)
- [Работа с цветом](/cpp/windows/working-with-color-image-editor-for-icons)
- [GDI (интерфейс графических устройств)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)