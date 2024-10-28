+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
date = {{ .Date }}
description = "Description par défaut pour {{ replace .File.ContentBaseName "-" " " | title }}."
+++
