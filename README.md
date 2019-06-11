# Form-Validation

# Hello, the goal of this project is to validate a form and make sure bots won't get their electronic hands on it

<div class="error_box inactive"></div>

<div class="info"><em>Required fields are marked with an asterisk (*)</em></div>

<form id="main_form" name="main_form" method="post" action="#" novalidate>
    <input name="form_id" type="hidden" value="570313">
    <input name="form:names" type="hidden"></input>
    <fieldset>
        <legend>Personal:</legend>
        <div class="form_row">
            <div class="label">
                <label for="First Name"><strong>First Name:</strong>*</label><span title="This is a required field"></span></div>
            <div class="input">
                <input type="text" id="first_name" name="first_name" placeholder="E.g. John" required="true" />
            </div>
        </div>
        <div class="form_row">
            <div class="label">
                <label for="Last Name"><strong>Last Name:</strong>*</label><span title="This is a required field"></span></div>
            <div class="input">
                <input type="text" id="last_name" name="last_name" placeholder="E.g. Smith" required="true" />
            </div>
        </div>
    </fieldset>
    <div class="form_row">
        <div class="label">
            <label for="Department"><strong>Email:</strong></label><span title="This is a required field"></span></div>
        <div class="input">
            <input type="email" id="email" name="email" required="true" />
        </div>
    </div>
    <div class="form_row">
        <div class="label">
            <label for="campus_affiliation"><strong>Campus Affiliation:*</strong></label><span title="This is a required field"></span></div>
        <div class="select">
            <select name="campus_affiliation" required="true">
                <option selected="true" value=""> - Select - </option>
                <option value="Faculty">Faculty</option>
                <option value="Staff">Staff</option>
                <option value="Undergraduate Student">Undergraduate Student</option>
                <option value="Graduate Student">Graduate Student</option>
            </select>
        </div>
    </div>
    <div class="form_row">
        <div class="label">
            <label for="question">A Question?*</label>
        </div>
        <div class="input_radio">
            <label for="q1">
                <input id="q1" name="question" type="radio" value="Yes" />Yes</label>
        </div>
        <div class="input_radio">
            <label for="q2">
                <input id="q2" name="question" type="radio" value="No" />No</label>
        </div>
    </div>
    </br>
    <div class="form_row">
        <div class="label">
            <label for="gender">Gender*</label>
        </div>
        <div class="input_checkbox">
            <label for="gender_male">
                <input name="gender" id="gender_male" type="checkbox" value="Male" />Male</label>
        </div>
        <div class="input_checkbox">
            <label for="gender_female">
                <input name="gender" id="gender_female" type="checkbox" value="Female" />Female</label>
        </div>
    </div>
    <input type="text" name="recaptcha-su_fix" id="recaptcha-su_fix" style="visibility: hidden;" />
    <div class="g-recaptcha" data-sitekey="6Lf_71oUAAAAAEa2DgPy0P_TKJQVBRV3LX1nMZNO"></div>
    <div align="center" class="form_row">
        <input align="center" name="btnSubmit" value="Submit" type="submit" />
    </div>
</form>


<link rel="stylesheet" media="screen" href="https://www.suffolk.edu/styles/validate.css">
<script type="text/javascript" src="https://www.suffolk.edu/scripts/validate.js"></script>
<script src="https://www.google.com/recaptcha/api.js"></script>

<script type="text/javascript">
(function() {
    var formName = "main_form";
    var formAction = "https://portalpro.suffolk.edu/webas/FormToEmail";
    var formreCaptcha = document.getElementById("recaptcha-su_fix");
    var formSettings = [{
        name: 'first_name',
        display: 'First Name',
        rules: 'required'
    }, {
        name: 'last_name',
        display: 'last Name',
        rules: 'required'
    }, {
        name: 'email',
        rules: 'valid_email|required'
    }, {
        name: 'campus_affiliation',
        display: 'Campus Affiliation',
        rules: 'required|min_length[2]'
    }, {
        name: "recaptcha-su_fix",
        display: "Im Not a Robot",
        rules: 'required',
        depends: function() {

            var response = grecaptcha.getResponse();
            if (response.length === 0) {
                formreCaptcha.value = "";
                return true;
            } else {
                formreCaptcha.value = "validated";
                return false;
            }

        }
    }];
    window.su_global.formAction = formAction;
    window.su_global.validateLogic(formName, formSettings);
})();
</script>
