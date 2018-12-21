---
title: Идентификаторы GUID и идентификаторы команд Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a1dbf79cc90f1f0ab0a7ff982fcabfa8d52150d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760146"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Идентификаторы GUID и идентификаторы команд Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Значения GUID и идентификатор команды, добавленные в среде разработки Visual Studio (IDE) определяются в файлах .vsct, установленные как часть Visual Studio SDK. Дополнительные сведения см. в разделе [IDE-Defined команд, меню и групп](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Дополнительные сведения о том, как работать с объектами интегрированной среды разработки, которые определены в vsct-файлах см. в разделе [расширение меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Поиск определения команды  
 Так как Visual Studio определяет более чем одна тысячная команды, нецелесообразно перечислить их все здесь. Вместо этого выполните следующие действия для этого найдите определение команды.  
  
#### <a name="to-locate-a-command-definition"></a>Для этого найдите определение команды  
  
1. В Visual Studio, откройте следующие файлы в *путь установки Visual Studio SDK*папку \VisualStudioIntegration\Common\Inc\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
    Большинство команд Visual Studio определяются в SharedCmdDef.vsct и ShellCmdDef.vsct. VsDbgCmdUsed.vsct определяет команды, относящиеся к отладчику, а Venusmenu.vsct команд, которые относятся к веб-разработки.  
  
2. Если команда в данный элемент меню, обратите внимание, точный текст пункта меню. Если команда является кнопки на панели инструментов, обратите внимание, текст подсказки, отображаемой при наведении на него.  
  
3. Нажмите клавиши CTRL + F, чтобы открыть **найти** диалоговое окно.  
  
4. В **найти** введите текст, записанный на шаге 2.  
  
5. Убедитесь, что **все открытые документы** отображается в **папка** поле.  
  
6. Нажмите кнопку **Найти далее** переключатель, пока текст выбран в `<Strings>` раздел [элемент Button](../../extensibility/button-element.md).  
  
    `<Button>` Элемент, который команда отображается в — определение команды.  
  
   Когда вы найдете определения команды, можно поместить копию команды на другом меню или панели инструментов, создав [элемент CommandPlacement](../../extensibility/commandplacement-element.md) с тем же установленным `guid` и `id` значения, что команда. Дополнительные сведения см. в разделе [группы кнопок для повторного использования создание](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Особые случаи  
 В следующих случаях текст меню или текст подсказки может не совпадать в определение команды.  
  
-   Пункты меню, которые включают это подчеркнутый символ, такие как **печати** на **файл** меню, в котором подчеркивается P.  
  
     Символы, которым предшествует символ «&» в именах элементов меню отображаются как подчеркнутый. Тем не менее, vsct-файлы создаются на языке XML, который использует символ «&» для указания специальных символов и требует, что знак амперсанда, который должен отображаться необходимо уточнять как&amp;". Таким образом, в vsct-файл **печати** команда появляется как "&amp;Печать".  
  
-   Команды, имеющие динамический текст, такие как **Сохранить** *текущее имя файла*и динамически созданные элементы меню, например элементы на **последние файлы** списка.  
  
     Нет надежного способа для поиска на динамический текст. Вместо этого найдите группу, на котором размещена нужную команду по журналу [идентификаторы GUID и идентификаторы из меню в Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) или [идентификаторы GUID и идентификаторы из Visual Studio панелей инструментов](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)и выполните поиск по Идентификатору этой группы. Если определение команды не ту группу, что его [родительского элемента](../../extensibility/parent-element.md), SharedCmdPlace.vsct и ShellCmdPlace.vsct (или VsDbgCmdPlace.vsct для команд отладчика) поиск `<CommandPlacement>` элемент, который задает родительский команда. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct ShellCmdPlace.vsct, находятся в *путь установки Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ папки.  
  
## <a name="see-also"></a>См. также  
 [Команды MenuCommand и OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Visual Studio Command Table (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

