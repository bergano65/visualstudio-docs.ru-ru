---
title: Команда "Запись вывода окна команд" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26ab9d7f19e56e35b5524472b4a7179b33d09cf0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651300"
---
# <a name="log-command-window-output-command"></a>Команда Log Command Window Output
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Копирует все входные и выходные данные из окна **Команда** в файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Необязательный параметр. Имя файла журнала. По умолчанию этот файл создается в папке профиля пользователя. Если такое имя файла уже существует, журнал добавляется в конец имеющегося файла. Если файл не указан, используется последний указанный файл. Если предыдущий файл отсутствует, создается файл журнала по умолчанию с именем cmdline.log.  
  
> [!TIP]
>  Чтобы изменить расположение для сохранения файла журнала, введите полный путь. Если этот путь содержит пробелы, заключите его в кавычки.  
  
## <a name="switches"></a>Переключатели  
 /on  
 Необязательный параметр. Запускает ведение журнала для окна **Команда** в указанном файле, добавляя в него новые данные.  
  
 /off  
 Необязательный параметр. Останавливает ведение журнала для окна **Команда**.  
  
 /overwrite  
 Необязательный параметр. Если указанный в аргументе `filename` файл совпадает с существующим файлом, он перезаписывается.  
  
## <a name="remarks"></a>Примечания  
 Если файл не указан, создается файл по умолчанию cmdline.log. По умолчанию эта команда имеет псевдоним Log.  
  
## <a name="examples"></a>Примеры  
 Этот пример создает файл журнала cmdlog и запускает ведение журнала команд.  
  
```  
>Tools.LogCommandWindowOutput cmdlog  
```  
  
 Этот пример останавливает ведение журнала команд.  
  
```  
>Tools.LogCommandWindowOutput /off  
```  
  
 Этот пример возобновляет ведение журнала команд в ранее использовавшемся файле.  
  
```  
>Tools.LogCommandWindowOutput /on  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
