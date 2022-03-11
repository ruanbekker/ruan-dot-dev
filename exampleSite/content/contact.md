+++
title = "Contact"
slug = "contact"
layout = "contact"
+++

Follow me on **Twitter**:

* [@ruanbekker](https://twitter.com/ruanbekker)

Reach out to me on **Slack**:

* [linux-hackers-slack](https://linux-hackers-slack.herokuapp.com)

Reach out to me via **Email**:

* [ruan@ruanbekker.com](mailto:ruan@ruanbekker.com)

<div class="container">
    <div class="row">
        <div class="col-lg-8 col-lg-offset-2 col-md-10 col-md-offset-1">
            {{ .Content }}
            <form action="https://formspree.io/f/xvozzpjz" method="POST">
                <label> Your email: <input type="email" name="email"></label>
                <label> Your message: <textarea name="message"></textarea></label>
                <!-- your other form fields go here -->
                <input type="text" name="_gotcha" style="display:none" />
                <button type="submit">Send</button>
            </form>
        </div>
    </div>
</div>
