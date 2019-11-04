---
title: Сопутствующие инструкции
description: Как участвовать в документации по Windows Mixed Reality.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: 934171f26571b3219bbe390aff44349fb6908f74
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437124"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="9ba2e-103">Документация для разработчиков Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9ba2e-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="9ba2e-104">Добро пожаловать в [общедоступный репозиторий документации для разработчиков Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="9ba2e-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="9ba2e-105">Все статьи, созданные или измененные в этом репозитории, **будут доступны для общего пользования.**</span><span class="sxs-lookup"><span data-stu-id="9ba2e-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="9ba2e-106">Документы Windows Mixed Reality теперь находятся на платформе docs.microsoft.com, которая использует Markdown с поддержкой GitHub (с функциями Маркдиг).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="9ba2e-107">По сути, содержимое, которое вы редактируете в этом репозитории, превращается в форматированные и стилизованные страницы, которые отображаются в https://docs.microsoft.com/windows/mixed-reality.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="9ba2e-108">На этой странице рассматриваются основные шаги и рекомендации по разработке, а также ссылки на основы Markdown.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="9ba2e-109">Благодарим вас за участие!</span><span class="sxs-lookup"><span data-stu-id="9ba2e-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="9ba2e-110">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="9ba2e-110">Before you start</span></span>

<span data-ttu-id="9ba2e-111">Если у вас ее еще нет, необходимо [создать учетную запись GitHub](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="9ba2e-112">Если вы являетесь сотрудником корпорации Майкрософт, свяжите свою учетную запись GitHub с псевдонимом Майкрософт на [портале Microsoft Open Source](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="9ba2e-113">Присоединяйтесь к организациям **"Microsoft"** и **"MicrosoftDocs"** .</span><span class="sxs-lookup"><span data-stu-id="9ba2e-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="9ba2e-114">При настройке учетной записи GitHub также рекомендуются следующие меры безопасности:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="9ba2e-115">Создайте [надежный пароль для учетной записи GitHub](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="9ba2e-116">Включите [двухфакторную проверку подлинности](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="9ba2e-117">Сохраняйте [коды восстановления](https://github.com/settings/auth/recovery-codes) в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="9ba2e-118">Обновите [Параметры общего профиля](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="9ba2e-119">Задайте свое имя и рассмотрите возможность установки *общедоступного адреса электронной почты* , чтобы *не показывать свой адрес электронной почты*.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="9ba2e-120">Рекомендуется отправить изображение профиля, так как эскиз будет отображаться на страницах документов, на которые вы участвуете.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="9ba2e-121">Если вы планируете использовать рабочий процесс командной строки, рассмотрите возможность настройки [диспетчера учетных данных Git для Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) , чтобы не вводить пароль каждый раз, когда вы вносите вклад.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="9ba2e-122">Эти шаги важны, так как система публикации привязана к GitHub, и вы будете перечислены как автор или участник для каждой статьи с помощью псевдонима GitHub.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="9ba2e-123">Изменение существующей статьи</span><span class="sxs-lookup"><span data-stu-id="9ba2e-123">Editing an existing article</span></span>

<span data-ttu-id="9ba2e-124">Используйте следующий рабочий процесс, чтобы обновить *существующую статью* с помощью GitHub в веб-браузере:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="9ba2e-125">Перейдите к статье, которую вы хотите изменить, в папке "Mixed-Reality-документы".</span><span class="sxs-lookup"><span data-stu-id="9ba2e-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="9ba2e-126">Нажмите кнопку Изменить (значок карандаша) в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="9ba2e-127">Это позволит автоматически разветвление удаляемой ветви из главной ветви.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Изменение статьи.](images/editpage.png)
3. <span data-ttu-id="9ba2e-129">Измените содержимое статьи (см. раздел ["Основные сведения о Markdown"](#markdown-basics) ниже для получения инструкций).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="9ba2e-130">Обновите метаданные в соответствии с актуальностью в верхней части каждой статьи:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="9ba2e-131">Title: это заголовок страницы, отображаемый на вкладке браузер при просмотре статьи.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="9ba2e-132">Так как это используется для SEO и индексирования, не следует изменять заголовок, если это не требуется (хотя это менее важно, прежде чем документация станет общедоступной).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="9ba2e-133">Описание. Напишите краткое описание содержимого статьи.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="9ba2e-134">Это помогает в SEO и Discovery.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="9ba2e-135">Автор: Если вы являетесь основным владельцем страницы, добавьте здесь свой псевдоним GitHub.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="9ba2e-136">MS. author: Если вы являетесь основным владельцем страницы, добавьте сюда свой псевдоним Майкрософт (вам не нужно @microsoft.com, просто псевдоним).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="9ba2e-137">MS. Date: обновите дату, если на страницу добавляется основное содержимое, но не для таких исправлений, как пояснение, форматирование, грамматика или Орфография.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="9ba2e-138">Ключевые слова: вспомогательные слова в SEO (оптимизация поисковой системы).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="9ba2e-139">Добавьте ключевые слова, разделенные запятыми и пробелами, которые относятся к вашей статье (но без знаков препинания после последнего ключевого слова в списке); Вам не нужно добавлять глобальные ключевые слова, которые применяются ко всем статьям, так как они управляются в других местах.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="9ba2e-140">После внесения изменений в статью прокрутите вниз и нажмите кнопку **предложить изменение файла** .</span><span class="sxs-lookup"><span data-stu-id="9ba2e-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="9ba2e-141">На следующей странице щелкните **создать запрос на вытягивание** для слияния автоматически созданной ветви с главной.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="9ba2e-142">Повторите описанные выше действия для следующей статьи, которую необходимо изменить.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="renaming-or-deleting-an-existing-article"></a><span data-ttu-id="9ba2e-143">Переименование или удаление существующей статьи</span><span class="sxs-lookup"><span data-stu-id="9ba2e-143">Renaming or deleting an existing article</span></span>

<span data-ttu-id="9ba2e-144">Если изменение приведет к переименованию или удалению существующей статьи, обязательно добавьте перенаправление.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-144">If your change will rename or delete an existing article, be sure to add a redirect.</span></span> <span data-ttu-id="9ba2e-145">Таким образом, любой пользователь, имеющий ссылку на существующую статью, останется в нужном месте.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-145">That way, anyone with a link to the existing article will still end up in the right place.</span></span> <span data-ttu-id="9ba2e-146">Перенаправления управляются файлом. openpublishing. Redirect. JSON в корне репозитория.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-146">Redirects are managed by the .openpublishing.redirection.json file in the root of the repo.</span></span>

<span data-ttu-id="9ba2e-147">Чтобы добавить перенаправление в. openpublishing. Redirect. JSON, добавьте запись в массив `redirections`.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-147">To add a redirect to .openpublishing.redirection.json, add an entry to the `redirections` array:</span></span>

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- <span data-ttu-id="9ba2e-148">`source_path` является относительным путем к старой статье, которую вы удаляете.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-148">The `source_path` is the relative repository path to the old article that you're removing.</span></span> <span data-ttu-id="9ba2e-149">Убедитесь, что путь начинается с `mixed-reality-docs` и заканчивается `.md`.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-149">Be sure the path starts with `mixed-reality-docs` and ends with `.md`.</span></span>
- <span data-ttu-id="9ba2e-150">`redirect_url` — это относительный общедоступный URL-адрес от старой статьи до новой статьи.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-150">The `redirect_url` is the relative public URL from the old article to the new article.</span></span> <span data-ttu-id="9ba2e-151">Убедитесь, что этот URL-адрес **не** содержит `mixed-reality-docs` или `.md`, так как он ссылается на общедоступный URL-адрес, а не путь к репозиторию.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-151">Be sure that this URL **does not** contain `mixed-reality-docs` or `.md`, as it refers to the public URL and not the repository path.</span></span> <span data-ttu-id="9ba2e-152">Допускается связывание с разделом в новой статье с использованием `#section`.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-152">Linking to a section within the new article using `#section` is allowed.</span></span> <span data-ttu-id="9ba2e-153">При необходимости вы также можете использовать абсолютный путь к другому сайту.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-153">You may also use an absolute path to another site here, if necessary.</span></span>
- <span data-ttu-id="9ba2e-154">`redirect_document_id` указывает, хотите ли вы иметь идентификатор документа из предыдущего файла.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-154">`redirect_document_id` indicates whether you would like to keep the document ID from the previous file.</span></span> <span data-ttu-id="9ba2e-155">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-155">The default is `false`.</span></span> <span data-ttu-id="9ba2e-156">Используйте `true`, если необходимо сохранить значение атрибута `ms.documentid` из перенаправленной статьи.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-156">Use `true` if you want to preserve the `ms.documentid` attribute value from the redirected article.</span></span> <span data-ttu-id="9ba2e-157">Если сохранить идентификатор документа, данные, такие как Просмотры страниц и ранжирования, будут переданы в целевую статью.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-157">If you preserve the document ID, data, such as page views and rankings, will be transferred to the target article.</span></span> <span data-ttu-id="9ba2e-158">Это следует делать, если перенаправление является главным переименованием, а не указателем на другую статью, охватывающую только часть одного и того же содержимого.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-158">Do this if the redirect is primarily a rename, and not a pointer to different article that only covers some of the same content.</span></span>

<span data-ttu-id="9ba2e-159">Если вы добавляете перенаправление, обязательно удалите и старый файл.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-159">If you add a redirect, be sure to delete the old file as well.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="9ba2e-160">Создание новой статьи</span><span class="sxs-lookup"><span data-stu-id="9ba2e-160">Creating a new article</span></span>

<span data-ttu-id="9ba2e-161">Используйте следующий рабочий процесс для *создания новых статей* в репозитории документации с помощью GitHub в веб-браузере:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-161">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="9ba2e-162">Создайте вилку из главной ветви MicrosoftDocs/Mixed-Reality (с помощью кнопки **ветвления** в правом верхнем углу).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-162">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Разветвление главной ветви.](images/forkbranch.png)
2. <span data-ttu-id="9ba2e-164">В папке "Mixed-Reality-документы" нажмите кнопку **создать новый файл** в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-164">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="9ba2e-165">Создайте имя страницы для статьи (используйте дефисы вместо пробелов и не используйте знаки препинания или апострофы) и добавьте ". md".</span><span class="sxs-lookup"><span data-stu-id="9ba2e-165">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Присвойте имя новой странице.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="9ba2e-167">Убедитесь, что новая статья создана в папке "Mixed-Reality-документы".</span><span class="sxs-lookup"><span data-stu-id="9ba2e-167">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="9ba2e-168">Это можно проверить, проверив "/миксед-реалити-Докс/" в новой строке имени файла.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-168">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="9ba2e-169">В верхней части новой страницы добавьте следующий блок метаданных:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-169">At the top of your new page, add the following metadata block:</span></span>

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. <span data-ttu-id="9ba2e-170">Заполните соответствующие поля метаданных в соответствии с инструкциями в [разделе выше](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-170">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="9ba2e-171">Запись содержимого статьи с помощью [основ Markdown](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-171">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="9ba2e-172">Добавьте раздел `## See also` в нижней части статьи со ссылками на другие важные статьи.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-172">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="9ba2e-173">По завершении нажмите кнопку **зафиксировать новый файл**.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-173">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="9ba2e-174">Щелкните **новый запрос на вытягивание** и объедините ветвь master в MicrosoftDocs/Mixed-Reality "Master" (убедитесь, что стрелка указывает на правильный способ).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-174">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Создание запроса на вытягивание из вилки в MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="9ba2e-176">Основы Markdown</span><span class="sxs-lookup"><span data-stu-id="9ba2e-176">Markdown basics</span></span>

<span data-ttu-id="9ba2e-177">Следующие ресурсы помогут узнать, как изменить документацию с помощью языка Markdown:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-177">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="9ba2e-178">Основы Markdown</span><span class="sxs-lookup"><span data-stu-id="9ba2e-178">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="9ba2e-179">Markdown-at-"Краткий справочник"</span><span class="sxs-lookup"><span data-stu-id="9ba2e-179">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="9ba2e-180">Дополнительные ресурсы для записи Markdown для docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="9ba2e-180">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="9ba2e-181">Добавление таблиц</span><span class="sxs-lookup"><span data-stu-id="9ba2e-181">Adding tables</span></span>

<span data-ttu-id="9ba2e-182">Из-за того, что таблицы стилей docs.microsoft.com, они не будут иметь границы или пользовательские стили, даже если вы попробуете использовать встроенный код CSS.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-182">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="9ba2e-183">Он будет работать в течение короткого периода времени, но в конечном итоге платформа будет выводить стили из таблицы.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-183">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="9ba2e-184">Итак, планируйте и старайтесь не усложнять таблицы.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-184">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="9ba2e-185">[Вот сайт, который упрощает Markdown таблицы](https://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-185">[Here’s a site that makes Markdown tables easy](https://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="9ba2e-186">[Расширение "документы Markdown" для Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) также упрощает создание таблиц, если вы используете [Visual Studio Code (см. ниже)](#using-visual-studio-code) , чтобы изменить документацию.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-186">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="9ba2e-187">Добавление изображений</span><span class="sxs-lookup"><span data-stu-id="9ba2e-187">Adding images</span></span>

<span data-ttu-id="9ba2e-188">Вам потребуется передать изображения в папку "Mixed-Reality-документы/изображения" в репозитории, а затем ссылаться на них соответствующим образом в статье.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-188">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="9ba2e-189">Изображения будут автоматически отображаться в полном размере. Это означает, что изображение имеет большой размер, а будет полностью заполнять всю ширину статьи.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-189">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="9ba2e-190">Поэтому рекомендуется предварительно изменить размер изображений перед их отправкой.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-190">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="9ba2e-191">Рекомендуемая ширина составляет от 600 до 700 пикселей, хотя размер снимка экрана или части снимка экрана, соответственно, должен быть больше или меньше.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-191">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9ba2e-192">Вы можете отправлять изображения только в разветвленный репозиторий перед слиянием.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-192">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="9ba2e-193">Таким образом, если вы планируете добавлять изображения в статью, вам потребуется [использовать Visual Studio Code](#using-visual-studio-code) , чтобы добавить изображения в папку "Images" вилки, или убедиться в том, что в веб-браузере выполнены следующие действия.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-193">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="9ba2e-194">Разветвление репозитория MicrosoftDocs/Mixed-Reality.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-194">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="9ba2e-195">Изменение статьи в вилке.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-195">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="9ba2e-196">В папку "Mixed-Reality-документы/изображения" в вилке отправлены изображения, на которые вы ссылаетесь в этой статье.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-196">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="9ba2e-197">Создан **запрос на вытягивание** для объединения вилки в главную ветвь MicrosoftDocs/Mixed-Reality.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-197">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="9ba2e-198">Чтобы узнать, как настроить собственный разветвленный репозиторий, следуйте инструкциям по [созданию новой статьи](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-198">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="9ba2e-199">Предварительный просмотр работы</span><span class="sxs-lookup"><span data-stu-id="9ba2e-199">Previewing your work</span></span>

<span data-ttu-id="9ba2e-200">При редактировании в GitHub через веб-браузер можно щелкнуть вкладку **Предварительный просмотр** в верхней части страницы, чтобы предварительно просмотреть работу перед фиксацией.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-200">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="9ba2e-201">Предварительный просмотр изменений в review.docs.microsoft.com доступен только для сотрудников Майкрософт</span><span class="sxs-lookup"><span data-stu-id="9ba2e-201">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="9ba2e-202">Сотрудники корпорации Майкрософт. После объединения публикаций в главную ветвь можно увидеть, как будет выглядеть документация, прежде чем она станет общедоступной на https://review.docs.microsoft.com/windows/mixed-reality?branch=master (Найдите статью, используя оглавление в левом столбце).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-202">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="9ba2e-203">Редактирование в браузере и редактирование с помощью настольного клиента</span><span class="sxs-lookup"><span data-stu-id="9ba2e-203">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="9ba2e-204">Редактирование в браузере является самым простым способом внесения быстрых изменений, однако существует несколько недостатков.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-204">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="9ba2e-205">Вы не получаете проверку орфографии.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-205">You don't get spell-check.</span></span>
- <span data-ttu-id="9ba2e-206">Вы не получаете никаких интеллектуальных связей с другими статьями (необходимо вручную ввести имя файла статьи).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-206">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="9ba2e-207">Загрузка и ссылки на изображения могут быть трудной.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-207">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="9ba2e-208">Если вы не будете работать с этими проблемами, вы можете использовать Настольный клиент, например [Visual Studio Code](https://code.visualstudio.com/) , с помощью нескольких [полезных расширений](#useful-extensions) для участия в документации.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-208">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="9ba2e-209">Использование Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9ba2e-209">Using Visual Studio Code</span></span>

<span data-ttu-id="9ba2e-210">По указанным [выше](#editing-in-the-browser-vs-editing-with-a-desktop-client)причинам вы можете использовать Настольный клиент для редактирования документации вместо веб-браузера.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-210">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="9ba2e-211">Рекомендуется использовать [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-211">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="9ba2e-212">"Настройка"</span><span class="sxs-lookup"><span data-stu-id="9ba2e-212">Setup</span></span>

<span data-ttu-id="9ba2e-213">Выполните следующие действия, чтобы настроить Visual Studio Code для работы с этим репозиторием:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-213">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="9ba2e-214">В веб-браузере:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-214">In a web browser:</span></span>
    1. <span data-ttu-id="9ba2e-215">Установите [Git для своего компьютера](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-215">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="9ba2e-216">Установите [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-216">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="9ba2e-217">[Разветвление MicrosoftDocs/Mixed-Reality](#creating-a-new-article) , если вы еще этого не сделали.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-217">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="9ba2e-218">В вилке щелкните **клонировать или Скачайте** и скопируйте URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-218">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="9ba2e-219">Создайте локальный клон разветвления в Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-219">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="9ba2e-220">В меню **вид** выберите пункт **Палитра команд**.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-220">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="9ba2e-221">Введите "Git: Clone".</span><span class="sxs-lookup"><span data-stu-id="9ba2e-221">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="9ba2e-222">Вставьте только что скопированный URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-222">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="9ba2e-223">Выберите место сохранения клона на компьютере.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-223">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="9ba2e-224">Щелкните **Открыть репозиторий** во всплывающем окне.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-224">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="9ba2e-225">Редактирование документации</span><span class="sxs-lookup"><span data-stu-id="9ba2e-225">Editing documentation</span></span>

<span data-ttu-id="9ba2e-226">Используйте следующий рабочий процесс, чтобы внести изменения в документацию с помощью Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-226">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="9ba2e-227">Все рекомендации по [редактированию](#editing-an-existing-article) и [созданию](#creating-a-new-article) статей, а также [основы редактирования Markdown](#markdown-basics), приведенные выше, применяются и при использовании Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-227">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="9ba2e-228">Убедитесь, что клонированная вилка обновлена в официальном репозитории.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-228">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="9ba2e-229">В веб-браузере создайте запрос на вытягивание, чтобы синхронизировать последние изменения от других участников в MicrosoftDocs/Mixed-Reality "Master" с вилкой (убедитесь, что стрелка правильно указывает).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-229">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Синхронизация изменений из MicrosoftDocs/Mixed-Reality с вилкой](images/sync_repos.PNG)
   2. <span data-ttu-id="9ba2e-231">В Visual Studio Code нажмите кнопку Синхронизация, чтобы синхронизировать обновленную вилку с локальным клоном.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-231">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Нажмите кнопку "Синхронизация"](images/sync_clone.png)
2. <span data-ttu-id="9ba2e-233">Создание или изменение статей в клонированном репозитории с помощью Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-233">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="9ba2e-234">Измените одну или несколько статей (при необходимости добавьте изображения в папку "изображения").</span><span class="sxs-lookup"><span data-stu-id="9ba2e-234">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="9ba2e-235">**Сохраните** изменения в **обозревателе**.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-235">**Save** changes in **Explorer**.</span></span>
      
      ![Выбор "сохранить все" в обозревателе](images/explorer_save.png)
   3. <span data-ttu-id="9ba2e-237">**Зафиксировать все** изменения в **системе управления версиями** (записать сообщение о фиксации при появлении запроса).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-237">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Выбор команды "фиксировать все" в системе управления версиями](images/source_control_commit.png)
   4. <span data-ttu-id="9ba2e-239">Нажмите кнопку **Синхронизация** , чтобы синхронизировать изменения с источником (вилка на GitHub).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-239">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Нажмите кнопку "Синхронизация"](images/sync_back.png)
3. <span data-ttu-id="9ba2e-241">В веб-браузере создайте запрос на вытягивание, чтобы синхронизировать новые изменения в вилке с MicrosoftDocs/Mixed-Reality "Master" (убедитесь, что стрелка указывает на правильный способ).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-241">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Создание запроса на вытягивание из вилки в MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="9ba2e-243">Полезные расширения</span><span class="sxs-lookup"><span data-stu-id="9ba2e-243">Useful extensions</span></span>

<span data-ttu-id="9ba2e-244">Следующие расширения Visual Studio Code очень полезны при редактировании документации:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-244">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="9ba2e-245">[Документация расширения Markdown для Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) — используйте **сочетание клавиш ALT + M** , чтобы открыть меню параметров создания документов, таких как:</span><span class="sxs-lookup"><span data-stu-id="9ba2e-245">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="9ba2e-246">Поиск и ссылки на отправленные образы.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-246">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="9ba2e-247">Добавьте форматирование, например списки, таблицы и связанные с документацией вызовы, такие как `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-247">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="9ba2e-248">Поиск и ссылки на внутренние ссылки и закладки (ссылки на определенные разделы на странице).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-248">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="9ba2e-249">Ошибки форматирования выделяются (наведите указатель мыши на ошибку, чтобы узнать больше).</span><span class="sxs-lookup"><span data-stu-id="9ba2e-249">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="9ba2e-250">[Средство проверки орфографии кода](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) — слова с ошибками будут подчеркнуты. Щелкните правой кнопкой мыши слово с ошибками, чтобы изменить его или сохранить в словаре.</span><span class="sxs-lookup"><span data-stu-id="9ba2e-250">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
