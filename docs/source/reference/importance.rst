.. module:: optuna.importance

optuna.importance
=================

The :mod:`~optuna.importance` module provides functionality for evaluating hyperparameter importances based on completed trials in a given study. The utility function :func:`~optuna.importance.get_param_importances` takes a :class:`~optuna.study.Study` and optional evaluator as two of its inputs. The evaluator must derive from :class:`~optuna.importance.BaseImportanceEvaluator`, and is initialized as a :class:`~optuna.importance.FanovaImportanceEvaluator` by default when not passed in. Users implementing custom evaluators should refer to either :class:`~optuna.importance.FanovaImportanceEvaluator`, :class:`~optuna.importance.MeanDecreaseImpurityImportanceEvaluator`, or :class:`~optuna.importance.PedAnovaImportanceEvaluator` as a guide, paying close attention to the format of the return value from the Evaluator's ``evaluate`` function.

.. note::

   :class:`~optuna.importance.FanovaImportanceEvaluator` takes over 1 minute when given a study that contains 1000+ trials.
   We published `optuna-fast-fanova <https://github.com/optuna/optuna-fast-fanova>`__ library,
   that is a Cython accelerated fANOVA implementation. By using it, you can get hyperparameter
   importances within a few seconds.
   If ``n_trials`` is more than 10000, the Cython implementation takes more than a minute, so you can use :class:`~optuna.importance.PedAnovaImportanceEvaluator` instead, enabling the evaluation to finish in a second.


.. autosummary::
   :toctree: generated/
   :nosignatures:

   get_param_importances
   FanovaImportanceEvaluator
   MeanDecreaseImpurityImportanceEvaluator
   PedAnovaImportanceEvaluator
