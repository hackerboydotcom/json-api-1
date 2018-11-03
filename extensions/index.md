---
layout: page
title: Extensions
show_sidebar: true
redirect_from: /profiles
---

JSON:API can be extended with profiles. These profiles enable an API to 
provide clients with information or functionality beyond that described 
in the base JSON:API specification.

Anyone can author a profile, and a single profile can be reused by multiple APIs.
Popular profiles may be implemented by off-the-shelf tools so that developers 
can seamlessly take advantage of the features these profiles provide.

## <a href="#existing-profiles" id="existing-profiles" class="headerlink"></a> Existing Profiles

{% for category in site.profile_categories %}
  <h3 id="#profiles-category-{{ category | slugify }}">
    {{ category }}
  </h3>
  <dl class="profiles-list">
    {% for profile in site.profiles %}
      {% if profile.categories contains category %}
        <dt><a href="{% include profile_url.md page=profile %}">{{ profile.name }}</a></dt>
        <dd>{{ profile.short_description }}</dd>
      {% endif %}
    {% endfor %}
  </dl>
{% endfor %}

## <a href="#profile-creation" id="profile-creation" class="headerlink"></a> Creating a New Profile

### <a href="#profile-creation-before" id="profile-creation-before" class="headerlink"></a> Before Creating a Profile

Please **check whether an existing profile fits your needs or could be amended
to fit your needs** before developing a new one.

- If a suitable profile already exists, consider using it. Having fewer, more
widely-deployed profiles makes it easier to create shared tooling.

- If there's an existing profile that could be amended to fit your needs,
consider asking the profile's author if they would be willing to modify it as
needed. Contact them through the information in their profile's registration
and give them some time to reply.

### <a href="#profile-creation" id="profile-creation" class="headerlink"></a> Authoring Your Profile

To author your profile, [download and fill out the template](/profile_template.md).

### <a href="#profile-register" id="profile-register" class="headerlink"></a> Register & Use Your Profile

Once your profile is ready, submit it to the JSON:API profile registry by creating
a pull request that contains your filled out template as an `index.md` file in a 
uniquely-named folder in the [`_profiles`](https://github.com/json-api/json-api/tree/gh-pages/_profiles) 
directory.
   
Your submission will be **approved within a week** by one of JSON:API's 
editors, assuming it meets the [profile extension requirements](/format/1.1/#profiles-authoring)
and follows the template above. The community may give you feedback on your
submission before it's approved, but you are not required to act on this 
feedback.

One caveat: if your profile defines a new, fundamental mechanism for doing
something "architectural" that other profiles may need to do too, it may be
held for extra consideration. This extra review is designed to check that the
proposed mechanism, were it to become a convention, wouldn't have problematic
ramifications.

Also, note that if the author of a registered profile dies, moves out of contact,
or otherwise can't or won't make changes that are important to the community,
the JSON:API's editors may reassign responsibility for the extension, to allow it
to continue to evolve.

By registering your profile:

1. it will be listed above for others to find and reuse.

2. it will be given an official url on jsonapi.org. This will be the URL you and
   others use to apply/identify the profile.

3. one of the JSON:API's editors will review your submission to check that it 
   follows the [profile extension requirements](/format/1.1/#profiles-authoring).
   These requirements can be a bit tricky, so getting an expert review ensures
   that your profile is legal for use with JSON:API.
   
Even though profile registration is strongly encouraged, it isn't mandatory.
If you choose not to register your profile, you can create your own URL, on 
a domain you control, and use that to identify your profile. You should 
self-host the filled out template at this URL.

## <a href="#prior-extensions" id="prior-extensions" class="headerlink"></a> Prior Extensions

JSON:API previously offered experimental support for a different extension
negotiation system than the one now in the specification, and it provided a
number of extensions for use with that old negotiation system. However, this
system was always experimental and has now been deprecated.

New APIs should not use the old system or any extensions designed for it.
APIs that already use these old extensions should direct clients to an
[earlier version of this page](https://github.com/json-api/json-api/blob/9c7a03dbc37f80f6ca81b16d444c960e96dd7a57/extensions/index.md)
as documentation.
