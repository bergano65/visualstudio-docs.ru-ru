---
title: GUIDs и идентионные идентионные обивки команды visual Studio (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708252"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUIDs и идентионные идентионности команд Visual Studio
Значения GUID и ID команд, включенных в интегрированную среду разработки Visual Studio (IDE), определяются в файлах .vsct, которые устанавливаются как часть SDK Visual Studio. Для получения дополнительной [информации](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)см.

 Для получения дополнительной [информации](../../extensibility/extending-menus-and-commands.md)о том, как работать с объектами IDE, которые определены в файлах *.vsct,* см.

## <a name="find-a-command-definition"></a>Найти определение команды
 Поскольку Visual Studio определяет более 1000 команд, нецелесообразно перечислять их все здесь. Вместо этого выполните следующие действия, чтобы найти определение команды.

### <a name="to-locate-a-command-definition"></a>Найти определение команды

1. В Visual Studio, откройте следующие файлы в *<Visual Studio SDK путь\>установки »VisualStudioIntegration»Common-Inc\\ * папку: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    Большинство команд Visual Studio определяются в *SharedCmdDef.vsct* и *ShellCmdDef.vsct.* *VsDbgCmdUsed.vsct* определяет команды, относящиеся к отладчику, а *Venusmenu.vsct* определяет команды, характерные для веб-разработки.

2. Если команда является элементом меню, обратите внимание на точный текст элемента меню. Если команда является кнопкой на панели инструментов, обратите внимание на текст инструментария, который появляется при паузе на ней.

3. Нажмите **Ctrl**+**F,** чтобы открыть поле **поиска** диалога.

4. В поле **«Найдите»** какое поле введите текст, который вы отметили в шаге 2.

5. Убедитесь, что **все открытые документы** отображаются в поле Look in the **Look.**

6. Нажмите кнопку **«Найти следующую»,** `<Strings>` пока текст не будет выбран в разделе [элемента кнопки.](../../extensibility/button-element.md)

    Элемент, `<Button>` в который отображается команда, — это определение команды.

   Когда вы нашли определение команды, можно поместить копию команды в другое меню или панель инструментов, создав [элемент CommandPlacement,](../../extensibility/commandplacement-element.md) который имеет те же `guid` значения и значения, что и `id` команда. Для получения дополнительной [информации см.](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>Особые случаи
 В следующих случаях текст меню или текст инструментария может не совпадать с определением команды.

- Элементы меню, включающие подчеркнутый символ, такие как команда **Print** в меню **файла,** в которой подчеркивается *P.*

     Персонажи, которым предшествует символ амперсанда (&) в названиях элементов меню, отображаются в качестве подчеркнутых. Тем не менее, *файлы .vsct* написаны в XML, который использует символ амперсанда (&) для обозначения специальных символов и требует, чтобы амперсэнд, который должен быть отображен, должен быть изложен как * &amp;и.* Таким образом, в файле *.vsct* команда **Print** отображается как * &amp;имитир; Печать*.

- Команды, имеющие динамический **Save** \<текст, такие\>как Сохранить текущее имя файла, и динамически сгенерированные элементы меню, такие как элементы из списка **последних файлов.**

     Надежного способа поиска динамического текста нет. Вместо этого, найти группу, которая хостов желаемой команды, посоветовавшись [с GUIDs и идентификаторы меню Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) или [GUIDs и идентификаторы Visual Studio панели инструментов](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md), и поиск по идентификатору этой группы. Если определение команды не имеет группу в качестве [родительского элемента,](../../extensibility/parent-element.md)поиск *SharedCmdPlace.vsct* и *ShellCmdPlace.vsct* (или *VsDbgCmdPlace.vsct* для команд отладчика) для `<CommandPlacement>` элемента, который устанавливает родительский элемент команды. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, и *VsDbgCmdPlace.vsct* находятся в * \<визуальной студии SDK путь\>установки "VisualStudio-Общие"Inc\\ * папки.

## <a name="see-also"></a>См. также

- [Таблица команд Visual Studio (.vsct) файлов](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Ссылка на схему VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
