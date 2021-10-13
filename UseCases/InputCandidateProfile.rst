.. _InputCandidateProfile:

UC: Input Candidate Profile
=================================================================================================================================

``InputCandidateProfile``

Triggers:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    User wants to enter information about a candidate

Pre-conditions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

Description:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. uml::

    @startuml

        actor "Recruiter" as Recruiter
        participant "UI" as UI
        participant "OCR" as OCR
        participant "Database" as Database

        alt OCR is used to input data
            Recruiter -> UI: Upload file
            UI -> OCR: Send File to OCR
            OCR -> OCR: Decode Input File
            OCR -> UI: Populate Corresponding Fields

            note over UI
                Data is displayed in the website as you type
            end note

        else

            Recruiter  -> UI: Enter Data to website

            note over UI
                Data is displayed in the website as you type
            end note
        end

        Recruiter -> UI: Click Save
        UI -> UI: Perform Data Validation

        alt Input data does not follow requirements
            UI -> Recruiter: Notify User of errors so that he/she can correct them.
        end

        UI -> Database: Store entry to Database

    @enduml

Post-conditions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    User profile is saved to the database.

Exceptions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

Notes and Issues:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

References to High-Level Requirements:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    - :ref:`FormatForDates`
    - :ref:`FormatForEmail`
    - :ref:`FormatForTelephoneNumbers`
    - :ref:`InputsComingFromOCRIsSupported`
    - :ref:`UserCanInputCandidateProfile`
