---
title: Сборка и очистка проектов и решений
description: В этой статье описывается создание проектов в Visual Studio для Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.topic: how-to
ms.openlocfilehash: a33b590290880a7e20e7c0ec44c0b12942b1240e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85939099"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Сборка и очистка проектов и решений

Выполните описанные в этой статье действия, чтобы научиться создавать, перестраивать и очищать некоторые или все проекты в решении.

> [!NOTE]
> Этот раздел относится к Visual Studio для Mac. Информацию о Visual Studio в Windows см. в статье [Создание и очистка проектов и решений в Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Сборка, перестроение или очистка всего решения

1. На **Панели решения** выберите узел решения:

    ![Выбор узла решения](media/compiling-and-building-image1.png)

2. В меню **Сборка** в строке меню выберите один из следующих пунктов:

    ![Выбор элемента меню "Собрать все"](media/compiling-and-building-image2.png)

    * Выберите **Собрать все**, чтобы скомпилировать только те файлы и компоненты проекта, которые были изменены с момента последней сборки.

    * Выберите **Перестроить все**, чтобы очистить решение, а затем выполнить сборку всех файлов и компонентов проекта.

    * Выберите **Очистить все**, чтобы удалить промежуточные и выходные файлы. После этого, когда останутся только файлы проекта и компонентов, можно собрать новые экземпляры промежуточных и выходных файлов.

## <a name="to-build-or-rebuild-a-single-project"></a>Сборка или перестроение одного проекта

1. Выберите проект на **Панели решения**.

2. Выберите меню **Сборка** в строке меню.

3. Выберите пункт "Сборка [имя_проекта]", "Перестроить [имя_проекта]" или "Очистить [имя_проекта]".

## <a name="to-stop-a-build"></a>Остановка сборки

Чтобы остановить сборку, выполните одно из указанных ниже действий.

* Щелкните красный квадрат в области состояния:

    ![Щелкните красный квадрат, чтобы остановить сборку](media/compiling-and-building-image3.png)

* В меню **Сборка** выберите команду **Остановить**.

* Нажмите клавиши **CMD+SHIFT+RETURN**.

## <a name="see-also"></a>См. также

- [Создание и очистка проектов и решений (Visual Studio в Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)