---
title: 'Ошибка: файл зависимости &#39;&#39; в проекте &#39;проекта&#39; не может быть скопирован в каталог запуска, так как он конфликтует с &#39;файлом зависимостей&#39; | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4fd45741585aaf82c82257999b40d6257e82d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656047"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Ошибка: файл зависимости &#39;&#39; в проекте &#39;проекта&#39; не может быть скопирован в каталог выполнения, так как он конфликтует с &#39;файлом зависимостей&#39;
Существует конфликт между ссылками. Чтобы запустить приложение, необходимо скопировать несколько разных файлов сборки с одинаковым именем файла в каталог bin. Каталог запуска не может разрешить конфликт, так как ни одна из зависимостей не является первичной ссылкой.

 Эта ошибка приведет к сбою процесса сборки.

 Дважды щелкните элемент списка задач, чтобы перейти к узлу ссылок проекта, в котором произошел конфликт.

 **Исправление ошибки**

- Сделайте одну из сборок прямой ссылкой проекта. Возможным недостатком этого подхода является то, что выбранная сборка может не работать со сборками, которым требуется другая версия указанной по ссылке сборки.

     \- или -

- Убедитесь, что обе копии сборки имеют строгие имена и находятся в глобальном кэше сборок. Это исключает необходимость копировать сборки в папку bin.

## <a name="see-also"></a>См. также:
 [Управление ссылками в](../ide/managing-references-in-a-project.md) [глобальном кэше](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) сборок проекта сборки [со строгими именами](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) сборка [управления версиями](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [Создание и удаление зависимостей проекта](../ide/how-to-create-and-remove-project-dependencies.md)