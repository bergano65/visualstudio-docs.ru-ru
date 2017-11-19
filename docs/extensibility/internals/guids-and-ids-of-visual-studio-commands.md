---
title: "Идентификаторы GUID и идентификаторов ID команд Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce546f36ed93f0f42bfd548c64f2a25669e162b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Идентификаторы GUID и идентификаторов ID команд Visual Studio
Значения GUID и ID команды, добавленные в среде разработки Visual Studio (IDE) определяются в vsct-файлами, которые устанавливаются как часть пакета SDK для Visual Studio. Дополнительные сведения см. в разделе [IDE-Defined команд, меню и группы](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Дополнительные сведения о работе с объектами интегрированной среды разработки, которые определены в vsct-файлами см. в разделе [расширение меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Поиск определения команды  
 Поскольку Visual Studio определяет несколько тысяч команд, нецелесообразно их все здесь перечислить. Вместо этого выполните следующие действия, чтобы найти определение команды.  
  
#### <a name="to-locate-a-command-definition"></a>Чтобы найти определение команды  
  
1.  В Visual Studio откройте следующие файлы в *путь установки Visual Studio SDK*папки \VisualStudioIntegration\Common\Inc\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     Большинство команд Visual Studio, определяются в SharedCmdDef.vsct и ShellCmdDef.vsct. VsDbgCmdUsed.vsct определяет команды, которые относятся к отладчика, а Venusmenu.vsct команды, которые относятся к веб-разработки.  
  
2.  Если команда является элемент меню, запомните точный текст элемента меню. Если команда является кнопка на панели инструментов, обратите внимание, текст подсказки, отображаемой при наведении на него.  
  
3.  Нажмите клавиши CTRL + F, чтобы открыть **найти** диалоговое окно.  
  
4.  В **найти** введите текст, записанный на шаге 2.  
  
5.  Убедитесь, что **все открытые документы** отображается в **папка** поле.  
  
6.  Нажмите кнопку **Найти далее** кнопку выбрать текст на `<Strings>` раздел [элемент Button](../../extensibility/button-element.md).  
  
     `<Button>` , Команда добавляется в элемент является определение команды.  
  
 При определении команды будут найдены, можно поместить копию команды на другом меню или панели инструментов путем создания [элемент CommandPlacement](../../extensibility/commandplacement-element.md) , имеет те же `guid` и `id` значения как команду. Дополнительные сведения см. в разделе [группы кнопок для повторного использования создание](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Особые случаи  
 В следующих случаях меню текст или текст всплывающей подсказки может не соответствовать возможности определения команды.  
  
-   Пункты меню, которые включают соответствующим подчеркнутым символом, такие как **печати** на **файл** меню, в котором подчеркивается P.  
  
     Символы, которым предшествует символ «&» в именах элементов меню отображаются как подчеркнутый. Тем не менее, vsct-файлами создаются на языке XML, который использует символ «&», чтобы указать специальные символы и требует, что должны быть написаны амперсанда, будет отображаться как&amp;". Таким образом, в vsct-файле **P**rint будет отображаться как "&amp;Печать".  
  
-   Команды, которые имеют динамический текст, такой как **Сохранить** *текущее имя файла*и динамически созданные элементы меню, такие как элементы на **последние файлы** списка.  
  
     Нет надежный способ поиска на динамический текст. Вместо этого найдите группу, на котором размещена нужную команду по журналу [идентификаторов GUID и идентификаторы из меню в Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) или [идентификаторы GUID и идентификаторы из Visual Studio панели инструментов](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)и выполните поиск по Идентификатору этой группы. Если определение команды не группе в качестве его [родительского элемента](../../extensibility/parent-element.md), SharedCmdPlace.vsct и ShellCmdPlace.vsct (или VsDbgCmdPlace.vsct для команд отладчика) поиск `<CommandPlacement>` задает родительский элемент команда. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct ShellCmdPlace.vsct, находятся в *путь установки Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ папки.  
  
## <a name="see-also"></a>См. также  
 [Команды MenuCommand и OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Таблицы команд Visual Studio (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)