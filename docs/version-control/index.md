---
layout: LandingPage
title: Управление версиями в Visual Studio | VSTS и Team Foundation Server
description: Руководство по началу работы с системами управления версиями в Visual Studio
keywords: VSTS, TFS, Version Control
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: landing-page
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.workload:
- multiple
ms.openlocfilehash: e37645f8960aae54907dffeb0bcb88848d9cd63f
ms.sourcegitcommit: 28909340cd0a0d7cb5e1fd29cbd37e726d832631
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44320583"
---
# <a name="version-control-in-visual-studio"></a>Управление версиями в Visual Studio

Системы управления версиями позволяют отслеживать изменения в коде по времени. Когда вы вносите изменения, система управления версиями создает моментальный снимок файлов. Этот снимок навсегда сохраняется в системе, благодаря чему вы можете повторно вызвать его в любое время. Visual Studio предоставляет такие системы управления версиями, как [Git](/azure/devops/repos/git/index?view=vsts) и [TFVC](/azure/devops/repos/tfvc/index?view=vsts) (система управления версиями Team Foundation). Чтобы выбрать одну из них, см. статью [Choosing the right version control for your project](/azure/devops/repos/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json) (Выбор системы управления версиями для вашего проекта).

## <a name="git"></a>Git
Git — наиболее часто используемая система управления версиями на сегодняшний день, которая стремительно становится стандартом в мире систем управления версиями. Это распределенная система управления версиями. Это значит, что репозиторий представляет собой полную локальную копию кода. Полнофункциональные локальные репозитории упрощают работу как в автономном, так и в удаленном режиме. Вы работаете в локальной среде, а затем синхронизируете свою копию репозитория с копией на сервере. Эта парадигма отличается от централизованных систем управления версиями, где клиенты должны синхронизировать код с сервером перед созданием новой версии кода.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://docs.microsoft.com/azure/devops/git/what-is-git">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Сведения о Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/share-your-code-in-git-vs-2017?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Начало работы с Git в Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/git/clone?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Клонирование существующего репозитория Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Подсистема контроля версий Team Foundation (TFVC) — это централизованная система управления версиями. Как правило, члены команды имеют на своих компьютерах разработки только одну версию каждого файла. Исторические данные ведутся только на сервере. Ветви основаны на путях и создаются на сервере.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/azure/devops/repos/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Сведения о TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Начало работы с TFVC в Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/azure/devops/repos/tfvc/get-code-reviewed-vs?toc=/visualstudio/version-control/toc.json&bc=/azure/devops/repos/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Проверка кода</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>


## <a name="resources"></a>Ресурсы

- [Книга Pro Git (Git для профессионалов)](https://git-scm.com/book/en/v2)
- [Переход с централизованной системы управления версиями на Git](https://docs.microsoft.com/azure/devops/git/centralized-to-git)
- [Переход с TFVC на Git](https://docs.microsoft.com/azure/devops/git/migrate-from-tfvc-to-git)